# otus_24
# Статическая и динамическая маршрутизация

Домашнее задание
OSPF
- Поднять три виртуалки
- Объединить их разными private network
1. Поднять OSPF между машинами средствами программных маршрутизаторов на выбор: Quagga, FRR или BIRD
2. Изобразить ассиметричный роутинг
3. Сделать один из линков "дорогим", но что бы при этом роутинг был симметричным

_____________________________________________________________________________________________________________

Домашняя работа
1. Поднять OSPF между машинами средствами программных маршрутизаторов на выбор: Quagga, FRR или BIRD.

Для выполнения задания выбран Quagga.

```vagrant up``` - для разворачивания стенда с OSPF. 

*Проверим маршруты на route1*

```ip r``` 

```vtysh``` - подключиться к рабочему демону Quagga.

![Img_alt](https://github.com/Edo1993/otus_24/blob/master/241.png)

*Проверим маршруты на route2*

![Img_alt](https://github.com/Edo1993/otus_24/blob/master/242.png)

*Проверим маршруты на route3*

![Img_alt](https://github.com/Edo1993/otus_24/blob/master/243.png)
