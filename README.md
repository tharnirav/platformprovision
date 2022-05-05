1. Enable cloudfunctions.googleapis.com & workflows.googleapis.com
2. Grant Project Creator Role to jp-poc-platform@appspot.gserviceaccount.com at Folder level
2. gcloud functions deploy create_project --runtime python37 --trigger-http --allow-unauthenticated
2. gcloud functions deploy execute_workflow --runtime python37 --trigger-http --allow-unauthenticated
   gcloud functions call execute_workflow --data '{"data":"'$DATA'"}'

{
  "createBucket": false,
  "needApproval": true,
  "projectName": "test-demo",
  "env": "dev",
  "Id": "deal1234"
}

curl -X POST -H "Authorization: Bearer $(gcloud auth print-access-token)" \
--header 'Content-Type: application/json' \
--data '{ "status": "APPROVED" }' \
https://workflowexecutions.googleapis.com/v1/projects/723035938579/locations/us-central1/workflows/project-provision-demo/executions/6870322c-0e10-4b29-9e6e-f35042f7ced1/callbacks/3b160743-3753-4d14-b229-25164f3f00c9_2a7ede75-df0d-498f-b806-3d5e1fa0796a
