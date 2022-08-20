# Helm Install, Upgrade & Rollback

```
 969  helm install mypywebapp mychart-py-app
  970  kubectl  get deploy,pod,svc,hpa
  971  ls
  972  vim mychart-py-app/values.yaml
  973  ls
  974  cp -rf mychart-py-app/values.yaml .
  975  ls
  976  kubectl delete pod pod/load-gen
  977  kubectl delete pod/load-gen
  978  ls
  979  vim values.yaml
  980  helm list
  981  helm upgrade -f values.yaml mypywebapp ./mychart-py-app
  982  helm list
  983  vim mychart-py-app/Chart.yaml
  984  ls
  985  vim mychart-py-app/values.yaml
  986  ls
  987  helm list
  988  helm upgrade  mypywebapp ./mychart-py-app
  989  helm list
  990  vim ./mychart-py-app/values.yaml
  991  ls
  992  helm upgrade  mypywebapp mychart-py-app
  993  ls
  994  vim mychart-py-app/values.yaml
  995  vim mychart-py-app/Chart.yaml
  996  s
  997  ls
  998  helm upgrade  mypywebapp mychart-py-app
  999  helm list
 1000  helm upgrade  mypywebapp mychart-py-app --force
 1001  helm upgrade -f ./mychart-py-app/values.yaml mypywebapp ./mychart-py-app
 1002  helm list
 1003  helm history
 1004  helm history  mypywebapp
 1005  helm rollback  mypywebapp
 1006  helm history  mypywebapp
 1007  helm rollback  mypywebapp 1
 1008  helm history  mypywebapp
 1009  helm rollback  mypywebapp 7
 1010  helm history  mypywebapp
```
