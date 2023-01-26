# Observability with metrics

1. I have used the metrics-server.yml to install a metrics server on the kubernetes cluster and to identify the service using the most memory. This file is in the bloatware file

2.  I launched the command: *kubectl top pods* to see the using of cpu and memory the differents pods
 bash-3.2$ kubectl top pods
NAME                                  CPU(cores)   MEMORY(bytes)   
bloaty-mcbloatface-58c98b98d8-8pv7k   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-8sl9z   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-97pxj   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-gd2s7   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-gh928   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-gwl66   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-hxqqj   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-jbbxp   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-jvcv7   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-kpclq   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-q554d   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-q66m2   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-qp4s7   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-rwwxc   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-scxsr   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-x24kk   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-zc2p9   1m           3Mi             
blue-8475cbdf46-5nqrp                 1m           3Mi             
blue-8475cbdf46-9lz8w                 1m           3Mi             
blue-8475cbdf46-s6dd7                 1m           3Mi             
canary-v1-64598c676f-7nhgh            0m           3Mi             
canary-v1-64598c676f-kq566            0m           3Mi             
canary-v1-64598c676f-vvq2h            0m           3Mi             
green-5cdd96c9b4-58hk2                1m           3Mi             
green-5cdd96c9b4-fg77d                1m           3Mi             
green-5cdd96c9b4-rhlkb                1m           3Mi             
hello-world-794458d64d-lc9j9          2m           19Mi

3. I have seen that the hello-world-794458d64d-lc9j9 pod using a lot of memory (19Mi)

4. I removed the hello-world-794458d64d-lc9j9 pod

bash-3.2$ kubectl delete pod hello-world-794458d64d-lc9j9
pod "hello-world-794458d64d-lc9j9" deleted

5. I checked another time *kubectl top pods* and in this time it isn't the hello-world-794458d64d-lc9j9 pod

bash-3.2$ kubectl top pods
NAME                                  CPU(cores)   MEMORY(bytes)   
bloaty-mcbloatface-58c98b98d8-8pv7k   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-8sl9z   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-97pxj   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-gd2s7   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-gh928   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-gwl66   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-hxqqj   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-jbbxp   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-jvcv7   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-kpclq   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-q554d   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-q66m2   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-qp4s7   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-rwwxc   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-scxsr   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-x24kk   1m           3Mi             
bloaty-mcbloatface-58c98b98d8-zc2p9   1m           3Mi             
blue-8475cbdf46-5nqrp                 1m           3Mi             
blue-8475cbdf46-9lz8w                 1m           3Mi             
blue-8475cbdf46-s6dd7                 1m           3Mi             
canary-v1-64598c676f-7nhgh            0m           3Mi             
canary-v1-64598c676f-kq566            0m           3Mi             
canary-v1-64598c676f-vvq2h            0m           3Mi             
green-5cdd96c9b4-58hk2                1m           3Mi             
green-5cdd96c9b4-fg77d                1m           3Mi             
green-5cdd96c9b4-rhlkb                1m           3Mi  
