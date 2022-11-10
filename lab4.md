Отчет по лабораторной работе #4 выполнил:
- Яковенко Виталий Андреевич
- РИ-300001
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | *| 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Задание 1
Используя видео-материалы практических работ 1-5 повторить реализацию
приведенного ниже функционала:
- 1 Практическая работа «Создание анимации объектов на сцене»
- 2 Практическая работа «Создание стартовой сцены и переключение
между ними»
- 3 Практическая работа «Доработка меню и функционала с остановкой
игры»
- 4 Практическая работа «Добавление звукового сопровождения в игре»
- 5 Практическая работа «Добавление персонажа и сборка сцены для
публикации на web-ресурсе»

Задание 2

Привести описание того, как происходит сборка проекта проекта под другие
платформы. Какие могут быть особенности?

Задание 3

Добавить в меню Option возможность изменения громкости (от 0 до 100%)
фоновой музыки в игре.

## Задание 1
создадим копию сцены и помняем анимацию дракона на статичную,которую мы заранее взяли из асета с драконами 
так же добавим на сцену гору и помести ее так чтобы дракон в игре распологался в незине.

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.1.png)

добавим на сцену текст с названием игры и покрасим его в красный и сделаем якорь на левый верхний угол .

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.2.png)

Чтоб меню игры выглядило поинтересне добавим облако из асета и создадим ему анимацию 
создаем контролер анимации и саму анимацию 
в файле анимации выбираем пункт position  полсле чего тыкаем на середину тайм лайна и изменяем кардинаты облака ,после чего добавляем ключ 
следующим шагов в контройлере анимаций подключаем созданную нами анимацию 
теперь мы можем изменять скорость проигрования анимациии 
теперь сцена выглядит так 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.3.png)

Теперь Сделаем меню Создадим три кнопки Play option quit и объединим их в пустом объекте майн меню
теперь мы можем перемещать разом три объекта 
Заменим спрайт кнопки на облачки 
итоговый вид 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.4.png)

теперь напишем код для кноки play и кнопки quit 
```C#
public class MainMenu : MonoBehaviour
{
    public void PlayGame(){
        SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex+1);
    }

    public void QuitGame(){
        Application.Quit();
    }
}
```
код для кнопки плэй переключает сцену на уровень выше 
а кнопка quit закрывант игру 
добавим действие при клике ,теперь кнопки работают .

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.6.png)

Для настройки кнопки option мы обойдемся без програмирования 
мы будем использовать флаг активности , при отключении флага объект исчезает ,а при включении появляется 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.6.png)

создадим кнопку back и поместим ее в пустй игровой объект setingmenu 
теперь настроим работу кнопок действи при клике на кнопку option выглядит так 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.8.png)

при нажатии на клавишу mainmenu перестает быть активным ,вместо этого активируется setting menu 

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.7.png)

кнопка back работает с точностью да наоборот.

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.9.png)

добавим звуковое сопровождение нашей игре 
в скрипте к ловле яйца и гранате добавим звук ловли или взрыва яйца 
в начале обявляем   public AudioSource audioSource;
после чего добавляем следующие строчки кода теперь при ловле и промахе будет воспроизводится звук 
```C#
 audioSource = GetComponent<AudioSource>();
           audioSource.Play();
 ```
 Сами звуки так же возьмем из асетов
 добавим фоновую музыку к maincamera подключаем audio souce 
 и добавим аудиофайл закицлим его чтобы музыка не заканчивалась 
 
 ![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.10.png)
 
 Теперь напишем скрипт паузы у сцене с игрой  
 
```C#
public class Pause : MonoBehaviour
{
    private bool paused = false;
    public GameObject panel;
    
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.Space)){
            if(!paused){
                Time.timeScale = 0;
                paused = true;
                panel.SetActive(true);
            }
            else{
                Time.timeScale = 1;
                paused = false;
                panel.SetActive(false);
            }
        }
        if(Input.GetKeyDown(KeyCode.Escape)){
            SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex-1);;
        }
    }
}

```
так же создадим обЪект текст который будет показывать что игра на паузе  
в итоге при нажатии на паузу время в игре останавливается и объекты перестат двигаться 
Вид игры на паузе

![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.10.png)

Для антуража добавим моделку мага в левыц угол экрана и источник освещения,чтобы выглядило поинтереснее
финальный вид игры 
## Задание 2
При сборке проекта на другую плотформу у меня не возникло ни каких проект ,но вот какие особености я нашел .

Developer builds — no fast builds!

Когда собираешь developer build есть возможность выбора между быстрой сборкой и быстрым исполнением. 
На самом деле быстрая сборка занимает почти такое же (громадное) 
количество времени и при этом, на большом проекте часто совсем не работает из-за нехватки памяти. Лучше её не использовать.

Strip engine code

Strip engine code — это галочка в настройках сборки, которая заставляет Unity выбрасывать из сборки неиспользуемые системные скрипты.
Это позволяет значительно сокращать итоговый объем сборки. Проблема здесь в том,
что если какой-то код используется только ассетами, попавшими в бандл, он тоже будет выброшен.
А итоговая сборка работать не будет. Причем exception будет абсолютно непонятный.
Ограничение на 512 mb

Полагаю, что не нужно выделять играм, собираемым под WebGL, больше памяти, 
чем 512mb,так как многие браузеры не позволяют выделить больше .
И саму игру нужно делать так, чтобы ей этого хватало. В идеале вообще оставить 256mb которые стоят по умолчанию.
## Задание 3
Для настройки звука в игру в меню настройек добавим слайдер
и напишем два кода один будет считывать значение слайдера и изменять значение громкости 
второй будет сохронять значение громкости даже после презапуска игры 
код слайдера 
```C#
public class SliderLevl : MonoBehaviour
{
    public Slider slider;
    public float oldVolume;
    void Start()
    {
        oldVolume = slider.value;
        if(!PlayerPrefs.HasKey("volume")) slider.value = 1;
        else slider.value = PlayerPrefs.GetFloat("volume");
    }

    // Update is called once per frame
    void Update()
    {
        if(oldVolume != slider.value)
        {
            PlayerPrefs.SetFloat("volume",slider.value);
            PlayerPrefs.Save();
            oldVolume = slider.value;
        }
    }
}
```
код уровня громкости 
```C#
public class AudioControler : MonoBehaviour
{
    public AudioSource auidio_;
    
    private void Start()
    {
        if(!PlayerPrefs.HasKey("volume"))
         {
            auidio_.volume = 1;
         }
    }

    // Update is called once per frame
    private void Update()
    {
        auidio_.volume = PlayerPrefs.GetFloat("volume");
    }
}
```
в итоге меню наастроек выглядит так 

## Выводы
![image](https://github.com/kiitiik/DA-in-GameDev-lab1/blob/main/img/4.12.png)

В итоге реализован основной функционал игры ,теперь осталось настройить sdk сервисы 

