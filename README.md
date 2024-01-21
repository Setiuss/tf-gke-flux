# tf-gke-flux

gsutil mb gs://kbot-tf-state 

tf init 

export TF_VAR_GITHUB_OWNER=

export TF_VAR_GITHUB_TOKEN=

export TF_VAR_GOOGLE_PROJECT=

tf apply

tf state list 

k get ns 

k get po -n flux-system 

flux get all 

flux logs -f 
 

flux create source git kbot \ 

    --url=https://github.com/setiuss/kbot \ 

    --branch=main \ 

    --namespace=demo \ 

    --export > github.com/setiuss/flux-gitops/clusters/demo/kbot-gr.yaml 

 

flux create helmrelease kbot \ 

    --namespace=demo \ 

    --source=GitRepository/kbot \ 

    --chart="./helm" \ 

    --interval=1m \ 

    --export > github.com/setiuss/flux-gitops/clusters/demo/kbot-hr.yaml 



flux get all -A 

k get po -n demo 

k describe po -n demo 
 

tf destroy 

tf state list  