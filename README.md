Wdrożenie aplikacji na platformie Azure

1) Zmieniamy plik konfiguracyjny deploymentu
app-name: '##appname##'
        slot-name: 'production'
        publish-profile: ${{ secrets.AZURE_WEBAPP_PUBLISH_PROFILE }}
        package: .
        
![1](https://github.com/m-winter/feedmail/blob/master/9.png)
        
2) Dodajemy nowy secret o nazwie AZURE_WEBAPP_PUBLISH_PROFILE, jako wartość dodajemy pobrane informacje z Azure publish Profile
![1](https://github.com/m-winter/feedmail/blob/master/8.png)

3) Deployujemy aplikacje przez Github Actions 
![1](https://github.com/m-winter/feedmail/blob/master/10.png)

4) W AppService Azura w Konfiguracji dodajemy 2 ustaiwenia aplikacji NODE_CONFIG z wartością {     "feedmail": {         "db": {             "url": "##DB CONNECTION##",              "name": "prod",              "options": {             "useUnifiedTopology": true              }         },         "logger": {             "level": "debug",             "filename": "./backend.log"         },         "mailgun": {             "domain": "##MAIL DOMAIN#",             "apiKey": "##MAILGUN API KEY##"         }       } }
 
 oraz NODE_ENV z wartością production
 ![1](https://github.com/m-winter/feedmail/blob/master/11.png)
 
5) TESTY

Landing Page
![1](https://github.com/m-winter/feedmail/blob/master/unknown.png)
Post /v1/user
![2](https://github.com/m-winter/feedmail/blob/master/2.jpg)
Get /v1/user
![3](https://github.com/m-winter/feedmail/blob/master/3.jpg)
Get /v1/mail
![4](https://github.com/m-winter/feedmail/blob/master/4.jpg)
Post /v1/mail
![5](https://github.com/m-winter/feedmail/blob/master/5.jpg)

