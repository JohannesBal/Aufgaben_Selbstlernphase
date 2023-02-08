# Aufgaben_Selbstlernphase

- vi lernen


- Wie kann ich meinen Cluster schützen abgesehen von dem Zertifikat, das ich in der kubeconfig habe?

Root-Rechte so wenig wie möglich vergeben - So viele wie nötig, so wenig wie möglich
Patches aktuell halten
Rollenbasierte Zugriffskontrolle - sowohl für Personen als auch Pods selbst
Seccomp (Linux kernel feature) sicherheitsprofile
etcd encryption 

- Was ist der Unterschied zwischen einem Deployment und einem Stateful-Set/Daemonset?

Ein Deployment beschreibt einen gewünschten Zustand(Soll-Zustand) und erstellt seinerseits ein Replicaset mit den Eigentschaften die über das Deployment festgelegt werden. Änderungen werden immer im Deployment vorgenommen. Da durch Änderungen im Deployment immer ein neues Replicaset erstellt wird. Das Replicaset sorgt für die Erstellung der Pods im Hintergrund. Die Pods die aus einem Deployment heraus erstellt werden sind absolut austauschbar falls Fehler auftreten. Die Pods werden absolut frei erstellt und beiFehlern gelöscht und neuerstellt.

Ein StatefulSet ist ähnlich einem Deployment allerdings mit einigen Abweichungen. So wird beispielsweise eine Reihenfolge für den Start der Pods eingehalten und sie sind einzigartig. Die Nummerierung der Pods erfolgt erfolgt bei 0 und endet bei N-1, wobei N die maximale Anzahl der angegebenen zu erstellenden Pods ist. 
Es gibt Abhängigkeiten in der Erstellung der Pods. Der Pod-1 wird nicht gestartet bevor Pod-0 läuft und bereit ist. Pod-2 wird erst gestartet wenn Pod-1 lauft und bereit ist. Sollt es zu einem Fehler kommen bei Pod-0 bevor Pod-2 gestartet ist, wird Pod-0 neugestartet und Pod-2 wird erst gestartet wenn Pod-0 wiedergestartet ist und läuft.
Beim Beenden von Pods geht es in umgekehrter Reihenfolge. Zuerst wird bei N-1 begonnen und als letztes wird Pod-0 beendet.

Ein Daemonset fügt allen bestehenden oder ausgewählten Node eine Kopie eines bestimmten Pods hinzu. Falls Nodes gelöscht werden, wird auch der hinzugefügte Pod entfernt. Eignet sich für Cluster-Speicherplatz, Log-Dateien zu sammeln oder Nodes zu überwachen.   

- Was ist ein Job? 
-   Ist das ein Pod oder Port? - Weder noch. Es ist ein eigenes Objekt, wie ein Service oder Deployment.

EIn Job ist ein Objekt, dass für eine Aufgabe erstellt wird. Dafür werden einer oder mehrere Pods erstellt. 

- Was macht der der (docker) expose-Befehl?

- Tanzu

- Kubernetes Concepts anschauen -> besonders Services, Loadbalancing ...
