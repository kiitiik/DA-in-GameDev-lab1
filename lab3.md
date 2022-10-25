Отчет по лабораторной работе #1 выполнил(а):

Яковенко Виталий Андреевич
РИ-300001 Отметка о выполнении заданий (заполняется студентом):
Задание	Выполнение	Баллы
Задание 1	*	60
Задание 2	*	20
Задание 3	*	20
знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:

к.т.н., доцент Денисов Д.В.
к.э.н., доцент Панов М.А.
ст. преп., Фадеев В.О.
N|Solid

Build Status

Структура отчета

Данные о работе: название работы, фио, группа, выполненные задания.
Цель работы.
Задание 1.
Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
Задание 2.
Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
Задание 3.
Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
Выводы.
✨Magic ✨
Цель работы: ознакомиться с основными функциями Unity и взаимодействием с объектами внутри редактора.

Лабораторная работа № 3. Реализация интерфейса пользователя

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
Задание 1
Начнем с реализации перемещение EnergyShild
для начало создаем новый файл скрипта и пишем для него следующий код 
```C#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using TMPro;

public class EnergyShield : MonoBehaviour
{
    public TextMeshProUGUI scoreGT;
    void Start() {
      GameObject  scoreGO = GameObject.Find("Score");
      scoreGT = scoreGO.GetComponent<TextMeshProUGUI>();
      scoreGT.text = "0";
    }

     void Update()
    {
        Vector3 mousePos2D = Input.mousePosition;
        mousePos2D.z = -Camera.main.transform.position.z;
        Vector3 mousePos3D = Camera.main.ScreenToWorldPoint(mousePos2D);
        Vector3 pos = this.transform.position;
        pos.x = mousePos3D.x;
        this.transform.position = pos;
    }
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

Выводы
Я скачал и настроил Unity для работы .Так же был создан проект в, котором затрагивались базовые элементы работы с Unity. https://github.com/kiitiik/Unity-lab-1

Powered by
BigDigital Team: Denisov | Fadeev | Panov
