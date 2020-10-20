# CATATAN KUBERNETES


### NODE ###

kubectl get node -> melihat semua node/minion <br>
kubectl describe node namanode -> melihat detail node



###   POD ###
kubectl get pod -> melihat semua pod  <br>
kubectl get pod -o wide -> melihat pod detail <br>
kubectl describe pod namapod -> melihat detail pod  <br>
kubectl create -f filepod.yaml -> membuat pod  <br>
    
### Mengakses POD / test doang  ###
       
kubectl port-forward namapod portAkses:portPod <br>
example <br>
kubectl port-forward namapod 8888:8080 // port akses ( local ) / port-pod ( port container) <br>

### LABEL ### 

kubectl get pod -> meliaht pod yang aktif <br>
kubectl get pod --show-labels -> melihat labels didalam pod <br>

kubectl label pod namapod key=value -> menambahkan label <br>
kubectl label pod namapod key=value --overwrite -> mengupdate label  <br>