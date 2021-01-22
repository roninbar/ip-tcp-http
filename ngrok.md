```mermaid
sequenceDiagram
autonumber
participant heroku as my.herokuapp.com
participant ngrokio as 4.tcp.ngrok.io
participant ngrok as ngrok.exe tcp 3306
participant mysql as mysql.exe <br/> (localhost:3306)
alt Direct connection is possible
heroku->>+mysql: connect(<server>:3306)
heroku->>mysql: send('SELECT * FROM `product`')
mysql->>heroku: send(query_results)
heroku->>mysql: disconnect()
mysql-->-heroku: x
else Direct connection is not possible
ngrok->>+ngrokio: connect(4.tcp.ngrok.io:443)
Note right of ngrok: "tcp://4.tcp.ngrok.io:17417 -> localhost:3306"
Note left of heroku: MYSQLHOST=4.tcp.ngrok.io <br/> MYSQLPORT=17417
heroku->>+ngrokio: connect(4.tcp.ngrok.io:17417)
ngrokio->>ngrok: send('.connect')
ngrok->>+mysql: connect(localhost:3306)
heroku->>ngrokio: send('SELECT * FROM `product`')
ngrokio->>ngrok: send('.send("SELECT * FROM `product`")')
ngrok->>mysql: send('SELECT * FROM `product`')
mysql->>ngrok: send(query_results)
ngrok->>ngrokio: send(`.send(${query_results})`)
ngrokio->>heroku: send(query_results)
heroku->>ngrokio: disconnect()
ngrokio-->-heroku: x
ngrokio->>ngrok: send('.disconnect')
ngrok->>mysql: disconnect()
mysql-->-ngrok: x
ngrok->>ngrokio: disconnect()
ngrokio-->-ngrok: x
end
```
