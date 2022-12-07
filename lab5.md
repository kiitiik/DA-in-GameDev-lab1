Отчет по лабораторной работе #4 выполнил:
- Яковенко Виталий Андреевич
- РИ-300001
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 |#| 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Цель работы: создание интерактивного приложения с рейтинговой системой
пользователя и интеграция игровых сервисов в готовое приложение.

## Задание 1

Используя видео-материалы практических работ 1-5 повторить реализацию
приведенного ниже функционала:

– 1 Практическая работа «Интеграции авторизации с помощью Яндекс
SDK»

– 2 Практическая работа «Сохранение данных пользователя на платформе
Яндекс Игры»

– 3 Практическая работа «Сбор данных об игроке и вывод их в интерфейсе»

– 4 Практическая работа «Интеграция таблицы лидеров»

– 5 Практическая работа «Интеграция системы достижений в проект»

1.

Для интеграции авторизации напиим код ,который будет проверять подключен ли yandexSDK
Создаем скрипт checkConectYandex  и пишим следющее :
```C#
public class CheckConnectYandex : MonoBehaviour
{
    private void OnEnable() => YandexGame.GetDataEvent += CheckSDK;
    private void OnDisable() => YandexGame.GetDataEvent += CheckSDK;

    void Start()
    {
        CheckSDK();
        
    }

    public void CheckSDK()
    {
        if (YandexGame.auth == true)
        {
            Debug.Log("User authorization ok");
        }
        else
        {
            Debug.Log("User not authorization");
            YandexGame.AuthDialog();
        }
    }
}
```
После проверки на вход мы увидим сообщение про статус аваторизации.
Если пользователь не прошел авторизацию ,то в яндекс играх вылезет менюшка для авторизации.
В яндекс кабинете разработчика ставим галочку напротив авторизации или лидерборд.

2.
Реализуем сохрание для пользователя 
в скрипте DragonPicker подключим библиотеку YG 
проверим подключена ли YandexSDK
в сохроняемые данные яндекс добовляеем score 

```C#
public void GetLoadSave()
    {
        Debug.Log(YandexGame.savesData.score);
    }

    public void UserSave(int currentScore)
    {
        YandexGame.savesData.score = currentScore;
        YandexGame.SaveProgress();
    }
```
Тепереь пользователь сохроняет количество набранных очков .

3.
Создадим табличку BestCore , где будем выводить лучший счет игрока 
в скрипте dragonPicker  в функции UserSave добавим код для сохранения лучшего счета .
```C#
if (currentScore > currentBestScore)
        {
            YandexGame.savesData.bestScore = currentScore;
        }
```
Для вывода имени пользователя добавим в канвас поле с текстом  Name 
Пишем скрипт, который будет находить  поле текста и вписывать в него имя пользователя 
```C#
public void GetLoadSave()
    {
        Debug.Log(YandexGame.savesData.score);
        GameObject  playerNamePrefabGUI = GameObject.Find("Name");
        playerName = playerNamePrefabGUI.GetComponent<TextMeshProUGUI>();
        playerName.text = YandexGame.playerName;
    }
```

4.
Добавим лидер борд в проекте 
```C#
YandexGame.NewLeaderboardScores("TopPlayers", score);
```
Зарегистрируем лидерборд в Yandex Консоли.

5.
копируем settings и переименовываем в achivments 
создаем текствове поле настраиваем на автоматическую регулировку текста .
в данные для сохранение добавляем масив строк achivMent
в checkConectYandex добавляем код ,кторый будет добавлять в listAchive новые достижения 
```C#
      if (YandexGame.savesData.achivMent[0] == null & !GameObject.Find("ListAchieve"))
        {

        }
        else
        {
            foreach (string value in YandexGame.savesData.achivMent)
            {
                GameObject.Find("ListAchieve").GetComponent<TextMeshProUGUI>().text = GameObject.Find("ListAchieve").GetComponent<TextMeshProUGUI>().text + value + "\n";
            }
        }
 ```
 А в dragonPicker добавляем само достиженеи и его сохранение в функции userSave 
 ```C#
 string[] achieveList;
            achieveList = YandexGame.savesData.achivMent;
            achieveList[0] = "Береги щиты!";
            UserSave(int.Parse(scoreGT.text),YandexGame.savesData.bestscore,achivList);
 ```
## Задание 2 
Описать не менее трёх дополнительных функций Яндекс SDK, которые могут быть интегрированы в игру.

1)Внутриигровые покупки. Позволяет зароботать делая платным внутриигровой контент .

2)Банерная реклама .Доход будет приходить просто за размещеную рекламу .

3)Показ рекламы после или до игровой сессии .

## Выводы
В этой работе мы разобрали ,как сохранять данные в яндексsdk ,создавать лидерборды и делать авчивки 

ссылка на hab с проектом https://github.com/kiitiik/Unity_lab_5
