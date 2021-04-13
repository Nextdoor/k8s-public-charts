## KubeQuotaAlmostFull

This alert telling you that the resources requested by all of the `Pods` in
your `Namespace` are close to the `Quota` limits that have been assigned. You
can inspect any quotas or limits placed on your `Namespace` like this:

    $ kubectl describe namespace my-namespace
    Name:         my-namespace
    Status:       Active

    Resource Quotas
     Name:             default-quotas
     Resource          Used     Hard
     --------          ---      ---
     limits.cpu        10500m   64
     limits.memory     18816Mi  128Gi
     requests.cpu      8500m    64
     requests.memory   16256Mi  128Gi
     requests.storage  105Gi    512Gi

    Resource Limits
     Type       Resource  Min  Max   Default Request  Default Limit  Max Limit/Request Ratio
     ----       --------  ---  ---   ---------------  -------------  -----------------------
     Container  cpu       -    8     0                0              -
     Container  memory    -    16Gi  128Mi            128Mi          -
