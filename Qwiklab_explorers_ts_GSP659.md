# Deploy Your Website on Cloud Run || [GSP659](https://www.cloudskillsboost.google/focuses/10445?parent=catalog) ||

# # Like, comment, share & Don't forget to subscribe [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN) 👍😄🤝

### Run the following Commands in CloudShell
```
export REGION=
```
```
#----------------------------------------------------start--------------------------------------------------#

echo "${YELLOW}${BOLD}Starting${RESET}" "${GREEN}${BOLD}Execution${RESET}"

gcloud auth list 

gcloud services enable artifactregistry.googleapis.com \
    cloudbuild.googleapis.com \
    run.googleapis.com

git clone https://github.com/googlecodelabs/monolith-to-microservices.git
cd ~/monolith-to-microservices

./setup.sh

cd ~/monolith-to-microservices/monolith

gcloud artifacts repositories create monolith-demo \
    --repository-format=docker \
    --location=$REGION \
    --description="Awesome Lab" 

gcloud auth configure-docker  --quiet 

gcloud builds submit --tag $REGION-docker.pkg.dev/${GOOGLE_CLOUD_PROJECT}/monolith-demo/monolith:1.0.0

echo "Y" | gcloud run deploy monolith --image $REGION-docker.pkg.dev/${GOOGLE_CLOUD_PROJECT}/monolith-demo/monolith:1.0.0 --region $REGION

gcloud run deploy monolith --image $REGION-docker.pkg.dev/${GOOGLE_CLOUD_PROJECT}/monolith-demo/monolith:1.0.0 --region $REGION --concurrency 1

gcloud run deploy monolith --image $REGION-docker.pkg.dev/${GOOGLE_CLOUD_PROJECT}/monolith-demo/monolith:1.0.0 --region $REGION --concurrency 80

cd ~/monolith-to-microservices/react-app/src/pages/Home
mv index.js.new index.js

cat ~/monolith-to-microservices/react-app/src/pages/Home/index.js

cd ~/monolith-to-microservices/react-app
npm run build:monolith

cd ~/monolith-to-microservices/monolith
gcloud builds submit --tag $REGION-docker.pkg.dev/${GOOGLE_CLOUD_PROJECT}/monolith-demo/monolith:2.0.0

gcloud run deploy monolith --image $REGION-docker.pkg.dev/${GOOGLE_CLOUD_PROJECT}/monolith-demo/monolith:2.0.0 --region $REGION

echo "${RED}${BOLD}Congratulations${RESET}" "${WHITE}${BOLD}for${RESET}" "${GREEN}${BOLD}Completing the Lab !!!${RESET}"

#-----------------------------------------------------end----------------------------------------------------------#
```

# Congratulations ..!!🎉  You completed the lab shortly..😃💯

# *Well done..!* 👏

# Thank you for visiting.... :) 🗯️

# [Qwiklab_Explorers_ts](https://youtube.com/@titashshil?si=RgamNu1dc9jVIbJN)
