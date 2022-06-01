IMAGETAG=bhanu_a15



## BUILD
docker build -t jaibw/website004:$IMAGETAG .
docker push jaibw/website004:$IMAGETAG



## Deploy
sed -i "s/username/$IMAGETAG/g" k8s-deploy.yaml
kubectl apply -f k8s-deploy.yaml
kubectl get svc | grep $IMAGETAG



echo "http://184.169.240.84:NODEPORT"
