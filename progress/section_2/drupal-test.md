NAME: sample-site
LAST DEPLOYED: Sat Sep 18 20:49:46 2021
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
*******************************************************************
*** PLEASE BE PATIENT: Drupal may take a few minutes to install ***
*******************************************************************

1. Get the Drupal URL:

  NOTE: It may take a few minutes for the LoadBalancer IP to be available.
        Watch the status with: 'kubectl get svc --namespace default -w sample-site-drupal'

  export SERVICE_IP=$(kubectl get svc --namespace default sample-site-drupal --template "{{ range (index .status.loadBalancer.ingress 0) }}{{.}}{{ end }}")
  echo "Drupal URL: http://$SERVICE_IP/"

2. Get your Drupal login credentials by running:

  echo Username: user
  echo Password: $(kubectl get secret --namespace default sample-site-drupal -o jsonpath="{.data.drupal-password}" | base64 --decode)



  main-drupal-site Password: YyO5NEm7Lm