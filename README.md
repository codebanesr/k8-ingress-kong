# Important note for this to work
Because Kong will be sitting outside the default namespace, be sure you also label the Kong namespace with istio-injection enabled as well

```kubectl label namespace kong istio-injection=enabled```

## Or else deploy pods in kong namespace as well


# Steps [till i don't find a way to use init containers to apply injection rules]
```
k apply -f k8-ingress-kong
At this phase pods wont have sidecar proxy injected in them, so I am adding the auto injection label


kubectl label namespace mongodb-namespace istio-injection=enabled

Once I delete all pods, when deployment tries to create pods, it ends up injecting the sidecar containers
k -n mongodb-namespace delete pods --all 
```


## Result [Traffic flow]
![Alt text](resources/traffic-flow.png?raw=true "Title")