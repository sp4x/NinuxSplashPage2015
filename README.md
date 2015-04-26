La splash page è hostata sul server `splash.spax.cs`, in alternativa è sufficiente scaricare il codice sulla root di un proprio server http.

Se si utilizza un proprio server occorre inserire l'URL appropriato nei file `splash.html` e `nodogsplash.conf`

    sed -i 's/splash.spax.cs/<vostro-server>/g' splash.html
    sed -i 's/splash.spax.cs/<vostro-server>/g' nodogsplash.conf
    
Per settare correttamente nodogsplash:

* In `nodogsplash.conf` impostare la corretta `GatewayInterface` e utilizzare il nomde nodo come `GatewayName`.
* Assicurarsi che il server http sia raggiungibile dalla subnet dell'hostspot
* Assicurarsi che la connessione alla porta 80 del server http sia consentita nel `nodogsplash.conf` in entrambe le sezioni `authenticated-users` e `preauthenticated-users`
* Installare nodogsplash sul router
    
        opkg update
        opkg install nodogsplash

* Copiare i 2 file sul router

        scp splash.html root@<vostro-router>:/etc/nodogsplash/htdocs
        scp nodogsplash.conf root@<vostro-router>:/etc/nodogsplash/
        
* abilitare e avviare il servizio sul router

        /etc/init.d/nodogsplash enable
        /etc/init.d/nodogsplash start