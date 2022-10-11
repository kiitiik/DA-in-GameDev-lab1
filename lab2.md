# Dragon Picker
Отчет по лабораторной работе #2 выполнил(а):
- Яковенко Виталий Андреевич
- РИ-300001
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Цель работы: создание интерактивного приложения и изучение принципов
интеграции в него игровых сервисов.
Задание 1
По теме видео практических работ 1-5 повторить реализацию игры на Unity.
Привести описание выполненных действий.
создаем новый проект Dragon picker в unity hub 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/Снимок%20экрана%202022-10-11%20163502.png)

Открываем проект для работы 
Изменем настройки камеры для корректного отображения сцены при запуске игры .

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/2.png)

Добавим готовые асэты библиотеки юнити 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/3.png)

В папке асэтов найдем префабы драконов и создадим дубликат , после перенесем его в папку Scenes
Переменуем дракона red в enemy 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.png)

Добавим дракону анимацию ,для этого создадим animator controller .
В асэтах найдем анимацию взмаха крыльями для нашего дракона,делаем дубликат и перекладываем в папку Scenes.
заходим в настройки animator controller и добавляем анимацию полета (перетаскиваем из Scenes)

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/5.png)

добавим на
в настройках дракона в меню аниматор в пункте avatar выбираем Dragon terrorBringerMeshAvatar
Добавим дракону скрипт ,чтобы он летал и переаодически сбрасывал яица .
смена направление происходит рандомно путеми зменение скорости на отрицательную (функция FixedUpdate)
Яица тоже сбрасываются в рандомный момент времени (функция DropEgg)

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/7.png)

Следующим шагом создаем яйцо 
создаем сферу с именем Dragonegg И меняем настройки ,чтобы сфера приняла яйцевидную форму 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/6.png)

К сфере подключаем Ridgidbody и включаем use gravity,чтобы наше яйцо падало 
Для того ,чтобы игры выглядила более привлекательной добовляем еще один асэт 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/8.png)

изменяем материал на яйце
Для того чтобы яица разбивались ,добавим panel и включим meshcolider в настройках включаем trigger

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/9.png)

Для того чтобы яйцо взрывалось пишем слудующий скрипт 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/10.png)

Добавим разбиение на частицы после взрыва и настроим их 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/11.png)

Также напишим скрипт который будет создовать три щиты при старте игры 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/12.png)


Следующее этап задание создать аккаунт на площадке яндекс игры и начать работать со строкой автора 
Аккаунт я создал при помощи яндекс почты ,а в строке автора ввел данные об игре .
## Задание 2
В проект, выполненный в предыдущем задании, добавить систему проверки
того, что SDK подключен (доступен в режиме онлайн и отвечает на запросы);
## Задание 3
- Произвести сравнительный анализ игровых сервисов Яндекс Игры и VK Game;
- Дать сравнительную характеристику сервисов,описатьфункционал;
- Описать их методы интеграции с Unity;
- Произвести сравнение, сделать выводы;
- Подготовить реферат по результатам выполнения.



##Выводы
В итоге наш дракон летает машет крыльями и сбрасывает яица , так же при старте игры спавняться energyshild .
В добавок был создан аккаунт на яндекс играх .

Plugin	README
Dropbox	[plugins/dropbox/README.md][PlDb]
GitHub	[plugins/github/README.md][PlGh]
Google Drive	[plugins/googledrive/README.md][PlGd]
OneDrive	[plugins/onedrive/README.md][PlOd]
Medium	[plugins/medium/README.md][PlMe]
Google Analytics	[plugins/googleanalytics/README.md][PlGa]
Powered by
BigDigital Team: Denisov | Fadeev | Panov
