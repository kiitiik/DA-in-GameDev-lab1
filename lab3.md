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

Цель работы: интеграция интерфейса пользователя в разрабатываемое

интерактивное приложение.

Задание 1.
Используя видео-материалы практических работ 1-5 повторить реализацию
игровых механик:

— 1 Практическая работа «Реализация механизма ловли объектов».

— 2 Практическая работа «Реализация графического интерфейса с

добавлением счетчика очков».

Задание 2.
— 3 Практическая работа «Уменьшение жизни. Добавление текстур».

— 4 Практическая работа «Структурирование исходных файлов в папке».

Задание 3.

— 5 Практическая работа «Интеграция игровых сервисов в готовое

## Задание 1

Начнем с реализации перемещение EnergyShild
для начало создаем новый файл скрипта и пишем для него следующий код 
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class EnergyShield : MonoBehaviour
{
     void Update()
    {
        Vector3 mousePos2D = Input.mousePosition;
        mousePos2D.z = -Camera.main.transform.position.z;
        Vector3 mousePos3D = Camera.main.ScreenToWorldPoint(mousePos2D);
        Vector3 pos = this.transform.position;
        pos.x = mousePos3D.x;
        this.transform.position = pos;
    }
}

```
сначала мы принимаем позицию иыши по корднате z , после чего представляим их для
трёхмерного пространства и изменяем позицию щита

тепреь наш щит перемещается за курсором мыши 
следующим шагом мы реализуем ловлю яиц для этого добавим метод OnCollisionEnter
где будет проверять объект и если это яйцо удалять .
Так же реализуем счетсик яиц пойманных игроком 
```C#
 private void OnCollisionEnter(Collision coll) {
        GameObject Collided = coll.gameObject;
        if (Collided.tag == "Draggon egg")
        {
            Destroy(Collided);
        }
        int score = int.Parse(scoreGT.text);
        score +=1;
        scoreGT.text =score.ToString();
    }
}
```
Для вывода количества яиц пойманных игроков добавим элемент ui text 
добовляем convas в main camera ,для коректного отображения очков 
помещаем его в угол экрана 
для работы с текстовым объектом подключим библиотеку TMPro
и напишем код для отображение очков игрока 
```C#
    public TextMeshProUGUI scoreGT;
    void Start() {
      GameObject  scoreGO = GameObject.Find("Score");
      scoreGT = scoreGO.GetComponent<TextMeshProUGUI>();
      scoreGT.text = "0";
    }
```
теперь когда мы ловим яйцо счетчик очков увеличивается на 1 
сделаем так чтобы яйцо удалялось при достижении определёной границы 
```C#
void Update()
    {
        if (transform.position.y < bottomY){
            Destroy(this.gameObject);
            DragonPIcker apScript = Camera.main.GetComponent<DragonPIcker>();
            apScript.DraggonEggDestroyed(); 
        }
    }
```

и в скрипте DragonPIcker допишем метод DraggonEggDestroyed
```C#
   public void DraggonEggDestroyed(){
        GameObject[] tDragonEggArray = GameObject.FindGameObjectsWithTag("Draggon egg");
        foreach (GameObject tGO in tDragonEggArray){
            Destroy (tGO);
        }
    }
```
создадим масив объектов исделаем цикл который проверят 
объект в масиве и если он его находит то удаляет его 

Задание 2

используем библеотеку для работы со сценой UnityEngine.SceneManagement
создадим лист объектов  shieldList для счета жизней 
при старте сцены мы записываем 3 щита в лист 
допишем в метод DraggonEggDestroyed код который будет удалять из листа щит при промахи и презапускать сцену
```C#
{
    int shieldIndex = shieldList.Count - 1;
        GameObject tShieldGo = shieldList[shieldIndex];
        shieldList.RemoveAt(shieldIndex);
        Destroy(tShieldGo);
        if (shieldList.Count ==0){
            SceneManager.LoadScene("_0Scene");
        
    }
```
и после того как счесчик достигает 0 сцена перезапускается на начальную 
игра начинается заново
добавим на сцену декаоротивные элементы ,для этого добавим асэты гор из юнити стора 
добавим гору на сцены и сменем ей кардинаты 
так же скачаем скай бокс и заменим его в настройках камеры 
итоговый результат 
отсртируем папки в проекте и удалим ненужные асэты 
итогвый результат 
Соберем билд проекта ,изменяем настройки игрока и качества 
качаем yandex game plagin и добавляем в проект 
нажимаем кнопку build and run собираем проект в папку 
готовый билд архивируем  и загружаем в наш черновик на yandexgame 
после проверки файла появится ссылка на игру ,где мы уже можем запустить игру в браузере и воспользоваться сервисами yandrexgame 


Выводы
. https://github.com/kiitiik/Unity-lab-1

Powered by
BigDigital Team: Denisov | Fadeev | Panov
