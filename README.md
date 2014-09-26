projecteCoreOs
==============

CoreOs


Primer commit , he pujat un projecte de github https://github.com/coreos/coreos-vagrant.git el qual 
et monta automàticament un clúster de CoreOs sobre el vagrant , els passos per a fer-ho estan dins del 
fitxer que el mateix paquet conté(README.md), tal i com es diu allí és molt important tenir les últimes
versions de virtualBox i vagrant ja que sinó dona un error al "pujar" la màquina virtual.
He modificat nomès el fitxer config.rb.sample per a fer el cluster més gran.



=============

Despres de provar diverses coses sembla que no es conecta be amb el fleet, tot i tenir el servei corrent dins dels nodes (amb errors pero),
continuare indagant mes tot i que ja he descartat que sigui una mala instalacio del etcd o fleet ja que he baixat les ultimes versions despres
dels darrers intents 


ErrorNode
core@core-01 ~ $ systemctl status fleet
● fleet.service - fleet daemon
   Loaded: loaded (/usr/lib64/systemd/system/fleet.service; static)
   Active: active (running) since Fri 2014-09-26 15:35:20 UTC; 19min ago
 Main PID: 1054 (fleetd)
   CGroup: /system.slice/fleet.service
           └─1054 /usr/bin/fleetd

Sep 26 15:35:20 core-01 systemd[1]: Starting fleet daemon...
Sep 26 15:35:20 core-01 systemd[1]: Started fleet daemon.
Sep 26 15:35:20 core-01 fleetd[1054]: INFO fleet.go:144: No provided or default config file found - proceeding without
Sep 26 15:35:20 core-01 fleetd[1054]: INFO server.go:137: Establishing etcd connectivity
Sep 26 15:35:20 core-01 fleetd[1054]: INFO server.go:148: Starting server components
Sep 26 15:35:20 core-01 fleetd[1054]: INFO engine.go:109: Engine leadership acquired
Sep 26 15:40:20 core-01 fleetd[1054]: INFO client.go:278: Failed getting response from http://localhost:4001/: unexpected EOF
Sep 26 15:40:20 core-01 fleetd[1054]: ERROR client.go:200: Unable to get result for {Watch /_coreos.com/fleet/job}, retrying in 100ms
Sep 26 15:40:20 core-01 fleetd[1054]: INFO client.go:278: Failed getting response from http://localhost:4001/: unexpected EOF
Sep 26 15:40:20 core-01 fleetd[1054]: ERROR client.go:200: Unable to get result for {Watch /_coreos.com/fleet/job}, retrying in 100ms
Sep 26 15:40:35 core-01 fleetd[1054]: ERROR event.go:91: etcd watcher {Watch /_coreos.com/fleet/job} returned error: unexpected end of JSON input
Sep 26 15:45:20 core-01 fleetd[1054]: ERROR event.go:91: etcd watcher {Watch /_coreos.com/fleet/job} returned error: unexpected end of JSON input
Sep 26 15:45:35 core-01 fleetd[1054]: ERROR event.go:91: etcd watcher {Watch /_coreos.com/fleet/job} returned error: unexpected end of JSON input
Sep 26 15:50:20 core-01 fleetd[1054]: ERROR event.go:91: etcd watcher {Watch /_coreos.com/fleet/job} returned error: unexpected end of JSON input
Sep 26 15:50:35 core-01 fleetd[1054]: ERROR event.go:91: etcd watcher {Watch /_coreos.com/fleet/job} returned error: unexpected end of JSON input


ErrorForaNode
hiro@hiro-x307:~/ProjecteCoreOs/projecteCoreOs/coreos-vagrant$ fleetctl list-machines
2014/09/26 17:58:32 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:32 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 100ms
2014/09/26 17:58:32 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:32 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 200ms
2014/09/26 17:58:32 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:32 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 400ms
2014/09/26 17:58:33 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:33 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 800ms
2014/09/26 17:58:34 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:34 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 1s
2014/09/26 17:58:35 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:35 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 1s
2014/09/26 17:58:35 ERROR fleetctl.go:171: error attempting to check latest fleet version in Registry: timeout reached
2014/09/26 17:58:35 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:35 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 100ms
2014/09/26 17:58:35 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:35 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 200ms
2014/09/26 17:58:35 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:35 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 400ms
2014/09/26 17:58:36 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:36 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 800ms
2014/09/26 17:58:37 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:37 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 1s
2014/09/26 17:58:38 INFO client.go:278: Failed getting response from http://127.0.0.1:4001/: dial tcp 127.0.0.1:4001: connection refused
2014/09/26 17:58:38 ERROR client.go:200: Unable to get result for {Get /_coreos.com/fleet/machines}, retrying in 1s
Error retrieving list of active machines: timeout reached


