# otuslinuxproff_hw37
iptables


<details>
<summary><h3>Задание</h3></summary>
Что нужно сделать?

   - реализовать knocking port

   - centralRouter может попасть на ssh inetrRouter через knock скрипт
    

   - добавить inetRouter2, который виден(маршрутизируется (host-only тип сети для виртуалки)) с хоста или форвардится порт через локалхост.
    запустить nginx на centralServer.
    пробросить 80й порт на inetRouter2 8080.
    дефолт в инет оставить через inetRouter.
    Формат сдачи ДЗ - vagrant + ansible
    реализовать проход на 80й порт без маскарадинга*
</details>


### Что сделано:
  - portknocking: c машины server на router, команда для доступа на него ``` knock 192.168.56.10 3000 4000 5000 && ssh vagrant@192.168.56.10```
  
 - сервер nginx: установлен на машине server и доступен на порту 8080, который проброшен на машину router на порт 80 и от туда проброшен vagrant-ом на localhost порт 8080. форвардинг портов настроен без MASQUERADE, он применяется для маршрутизации
 
 - добавил default route через машину router и интерфейc дополнительной приватной сети eth1. Вагрантовский маршрут не удалял т.к через него работает ansible. Удалить коммандой  ``` sudo ip route flush dev eth0 ``` 
 
 ### Запуск:
   ``` vagrant up ```
   
 ### Screenshots:
 
 ![image](https://user-images.githubusercontent.com/59445051/229614779-fd29230e-aac2-4ea1-9ad9-e37a8ee91b65.png)


![image](https://user-images.githubusercontent.com/59445051/229609027-b83301c4-2598-45b8-806c-3eef8a0b2c76.png)

![image](https://user-images.githubusercontent.com/59445051/229615382-768899b2-2305-4867-9b7a-23929aa01db7.png)
