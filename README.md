
# Приветствую!

Данный проект написан на ___[JAVA CORE](https://www.digitalocean.com/community/tutorials/core-java-tutorial)___ 
без использования дополнительных инструментов, в нём я старался отточить навыки применения принципов ___[SOLID][1]___.

Как у меня получилось, оставлю оценку за вами. :smile::ok_hand:

Данная мини программка несёт развлекательный характер. Запустив этот код вы можете поучаствовать в гонках.

Все результаты работы кода выводятся в консоль.

Что именно и как происходит в коде я опишу ниже.
***
Разберём все классы по отдельности и их связи между собой.
***
## ___[interface](https://www.digitalocean.com/community/tutorials/interface-in-java) [Vehicle](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Vehicle.java)___

Код в ___[interface](https://www.digitalocean.com/community/tutorials/interface-in-java) [Vehicle](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Vehicle.java)___ (Транспортное средство), который определяет некоторые методы, связанные с характеристиками транспортного средства.\
Вот описание каждого метода:
- `getMaxSpeed()`: Этот метод возвращает максимальную скорость транспортного средства в виде целого числа.
- `getAcceleration()`: Этот метод возвращает ускорение транспортного средства в виде числа с плавающей запятой ___[(double)](https://www.w3schools.com/java/java_data_types.asp)___.
- `getNitroLevel()`: Этот метод возвращает уровень нитро транспортного средства в виде целого числа.

___Interface Vehicle___ определяет только сигнатуры методов, но не их реализацию.
Классы, которые реализуют этот интерфейс, должны предоставить конкретную реализацию для каждого из этих методов.

Вот какому принципу соответствует `interface Vehicle`:
- Принципу интерфейсов ___(Interface Segregation Principle - ISP)___:\
ISP гласит, что клиенты не должны зависеть от интерфейсов, которые они не используют. В данном случае,
`interface Vehicle` определяет только методы, связанные с характеристиками транспортного средства. 
Это позволяет клиентам, которым не нужны все эти характеристики, не реализовывать их.

Таким образом, принцип ___ISP___ помогает разделить интерфейсы на более мелкие и специфичные, чтобы избежать ненужной зависимости и избыточности кода.
***
## ___Class [Car](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Car.java)___

___Class [Car](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Car.java)___ является реализацией `interface Vehicle` и представляет собой модель автомобиля.\
Описание полей класса:
- `maxSpeed` - максимальная скорость автомобиля (целочисленное значение).
- `acceleration` - ускорение автомобиля (вещественное значение).
- `score` - текущий счет автомобиля (целочисленное значение).
- `kilometersTravelled` - пройденное расстояние в километрах (целочисленное значение).
- `nitroLevel` - уровень нитро автомобиля (целочисленное значение).

___[Constructor](https://www.digitalocean.com/community/tutorials/constructor-in-java)___ `class Car` принимает параметры `maxSpeed`, `acceleration`, `score` и `nitroLevel` и инициализирует соответствующие поля объекта.\
Методы класса:\
- `getMaxSpeed()` - возвращает максимальную скорость автомобиля.
- `getAcceleration()` - возвращает ускорение автомобиля.
- `getScore()` - возвращает текущий счет автомобиля.
- `setScore(int score)` - устанавливает новое значение для счета автомобиля.
- `getKilometersTravelled()` - возвращает пройденное расстояние в километрах.
- `setKilometersTravelled(int kilometersTravelled)` - устанавливает новое значение для пройденного расстояния.
- `getNitroLevel()` - возвращает уровень нитро автомобиля.

___Class Car___ реализует `interface Vehicle`, что означает, что он должен предоставлять реализацию всех методов, определенных в интерфейсе. 
В данном случае, `class Car` реализует методы `getMaxSpeed()`, `getAcceleration()` и `getNitroLevel()`.
Этот класс предоставляет информацию о характеристиках автомобиля, таких как максимальная скорость, ускорение и уровень нитро. 
Он также содержит дополнительные поля, такие как счет и пройденное расстояние, а также методы для работы с этими полями.

___Class Car___ соответствует принципам ___[SOLID][1]___, а именно:
- Принцип единственной ответственности ___(Single Responsibility Principle - SRP)___:\
___Class Car___ имеет только одну ответственность - представлять автомобиль. Он содержит только методы и поля, связанные с автомобилем, такие как максимальная скорость, ускорение, очки, пройденные километры и уровень нитро. 
Он не содержит логики, связанной с другими аспектами системы.


- Принцип открытости/закрытости ___(Open/Closed Principle - OCP)___:\
___Class Car___ открыт для расширения (путем реализации `interface Vehicle`), но закрыт для модификации. 
Если мы хотим добавить новый тип транспортного средства, мы можем создать новый класс, реализующий `interface Vehicle`, без изменения `class Car`.


- Принцип подстановки Барбары Лисков ___(Liskov Substitution Principle - LSP)___:\
___Class Car___ является подтипом `interface Vehicle` и может быть использован везде, где ожидается объект типа ___Vehicle___. 
Это означает, что код, который работает с ___Vehicle___, будет работать и с объектами типа ___Car___ без необходимости внесения изменений.


- Принцип инверсии зависимостей ___(Dependency Inversion Principle - DIP)___:\
___Class Car___ зависит от абстракции, представленной `interface Vehicle`, а не от конкретной реализации. 
Это позволяет легко заменить `class Car` другой реализацией `interface Vehicle`, если потребуется.


- Принцип разделения интерфейса ___(Interface Segregation Principle - ISP)___:\
___Class Car___ реализует только методы, которые ему необходимы из `interface Vehicle`. 
Он не имплементирует ненужные методы, что позволяет избежать ненужной зависимости от функциональности, которая не используется.

В целом, `class Car` соответствует принципам ___[SOLID][1]___, что делает его гибким, расширяемым и легко поддерживаемым компонентом системы.
***
## ___Class [Constants](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Constants.java)___

___Class [Constants](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Constants.java)___ является финальным ___[(final)](https://www.geeksforgeeks.org/final-keyword-in-java/)___ и содержит только ___[static](https://www.digitalocean.com/community/tutorials/static-keyword-in-java)___ поля и ___[constants](https://www.edureka.co/blog/what-is-java-constant/)___. Он предназначен для хранения различных констант, используемых в приложении.\
Данный файл `Constants.java` соответствует принципу ___[SOLID][1]___:
- Принципу единственной ответственности ___(Single Responsibility Principle)___:\
Принцип единственной ответственности гласит, что каждый класс должен иметь только одну причину для изменения. 
В данном случае, `class Constants` отвечает только за хранение констант, которые используются в других частях программы. 
Он не содержит логики или функциональности, а только определения констант.
Это соответствие принципу ___[SOLID][1]___ обеспечивает легкость поддержки и изменения кода. 
Если потребуется изменить значение какой-либо константы, это можно сделать только в одном месте - в `class Constants`. 
Это уменьшает вероятность ошибок и облегчает понимание кода другим разработчикам.

Таким образом, `class Constants` соответствует принципу единственной ответственности, так как его единственная ответственность - хранение констант.
***
## ___Class [Menu](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Menu.java)___

___Class [Menu](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Menu.java)___ является перечислением ___[(enum)](https://www.geeksforgeeks.org/enum-in-java/)___ и представляет меню с опциями для игры.\
Он содержит следующие элементы:
- ___Константы___:
    - `START_RACE`: Представляет опцию "Устроить заезд" с соответствующим текстом и кодом.
    - `SHOW_STATISTICS`: Представляет опцию "Показать статистику" с соответствующим текстом и кодом.
    - `STOP_GAME`: Представляет опцию "Закончить игру" с соответствующим текстом и кодом.
    - `DEFAULT`: Представляет опцию по умолчанию с текстом "Сделайте ввод соответствующий пунктам меню" и кодом "-1".
- ___Приватные статические поля___:
    - `WHAT_YOU_CHOOSE`: Строка с текстом "Что выберете?".
- ___Приватные поля___:
    - `title`: Строка с заголовком опции меню.
    - `code`: Строка с кодом опции меню.
- ___Конструктор___:
    - `Menu(String title, String code)`: Конструктор, который принимает заголовок и код опции меню и инициализирует соответствующие поля.
- ___Методы___:
    - `printTitle()`: Выводит заголовок опции меню.
    - `print()`: Выводит все опции меню.
    - `getMenuByCode(String code)`: Возвращает опцию меню по заданному коду.
    - `getTitle()`: Возвращает заголовок опции меню.

___Class Menu___ предоставляет удобный способ работы с меню игры, позволяя выводить опции, получать опцию по коду и получать заголовок опции.

___Class Menu___ соответствует принципам ___[SOLID][1]___ следующим образом:
- Принцип единственной ответственности ___(Single Responsibility Principle - SRP)___:\
___Class Menu___ имеет только одну ответственность - представлять меню с определенными пунктами и их кодами. 
Он определяет пункты меню, их заголовки и коды, а также предоставляет методы для получения заголовка и печати меню. 
Это соответствует принципу ___SRP___, так как класс имеет только одну причину для изменения - изменение самого меню.


- Принцип открытости/закрытости ___(Open/Closed Principle - OCP)___:\
___Class Menu___ закрыт для изменений, так как он является перечислением ___(enum)___ и не предоставляет возможности для наследования или изменения своего поведения. 
Однако, новые пункты меню могут быть добавлены путем создания новых экземпляров перечисления Menu. 
Это соответствует принципу ___OCP___, так как класс открыт для расширения (добавления новых пунктов меню), но закрыт для изменений (не требует изменения существующего кода).


- Принцип подстановки Барбары Лисков ___(Liskov Substitution Principle - LSP)___:\
В данном случае, принцип ___LSP___ не применим, так как `class Menu` не является базовым классом и не имеет наследников.


- Принцип разделения интерфейса ___(Interface Segregation Principle - ISP)___:\
В данном случае, принцип ___ISP___ не применим, так как `class Menu` не реализует интерфейсы.


- Принцип инверсии зависимостей ___(Dependency Inversion Principle - DIP)___:\
В данном случае, принцип ___DIP___ не применим, так как `class Menu` не зависит от абстракций или интерфейсов.

Таким образом, `class Menu` соответствует принципам ___[SOLID][1]___, особенно принципу единственной ответственности и принципу открытости/закрытости.
***
## ___Class [Race](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Race.java)___

___Class [Race](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Race.java)___ представляет гоночное соревнование между двумя автомобилями. Он содержит поля для вашего автомобиля `yourCar`, автомобиля оппонента `opponentCar` и расстояния `distance`.\
___Class Race___ имеет следующие методы:
- `getYourCar()`: Возвращает ваш автомобиль.
- `setYourCar(Car yourCar)`: Устанавливает ваш автомобиль.
- `getOpponentCar()`: Возвращает автомобиль оппонента.
- `setOpponentCar(Car opponentCar)`: Устанавливает автомобиль оппонента.
- `getDistance()`: Возвращает расстояние гонки.
- `setDistance(int distance)`: Устанавливает расстояние гонки.
- `printRaceResults()`: Выводит результаты гонки, включая количество очков вашего автомобиля и пройденное расстояние.
- `logicOfTheRace()`: Определяет логику гонки и возвращает количество очков, набранных вашим автомобилем. Если ваш автомобиль выигрывает короткую гонку или длинную гонку, возвращается максимальная скорость автомобиля. Если скорости автомобилей равны, возвращается 0 очков. Если ваш автомобиль проигрывает, но сохраняет очки, возвращается 0 очков. Если ваш автомобиль проигрывает и теряет очки, возвращается отрицательное количество очков.
- `printFlag()`: Выводит флаг гонки.
___Class Race___ использует `class Race`, который должен быть определен в отдельном файле.

Данный `class Race` соответствует принципам ___[SOLID][1]___:\
- Принцип единственной ответственности ___(Single Responsibility Principle - SRP)___:\
___Class Race___ имеет только одну ответственность - управление гонкой.
Он содержит методы для установки автомобилей, установки расстояния, вывода результатов гонки и логики гонки.
Каждый метод выполняет только одну задачу, что соответствует ___SRP___.


- Принцип открытости/закрытости ___(Open/Closed Principle - OCP)___:\
___Class Race___ открыт для расширения, так как можно добавить новые методы или функциональность для улучшения гонки, но он закрыт для изменений, так как существующий код не требует изменений при добавлении новых функций.


- Принцип подстановки Барбары Лисков ___(Liskov Substitution Principle - LSP)___:\
___Class Race___ использует абстракцию ___Car___ для работы с объектами автомобилей. 
Это позволяет подставлять любой подкласс ___Car___ без изменения кода `class Race`. 
Например, если бы был создан подкласс `ElectricCar`, его можно было бы использовать вместо ___Car___ без изменения кода `class Race`.


- Принцип разделения интерфейса ___(Interface Segregation Principle - ISP)___:\
___Class Race___ не реализует интерфейсы, поэтому этот принцип не применяется непосредственно к данному классу.


- Принцип инверсии зависимостей ___(Dependency Inversion Principle - DIP)___:\
___Class Race___ зависит от абстракции ___Car___, а не от конкретной реализации. Это позволяет легко заменять различные типы автомобилей без изменения кода `class Race`.

В целом, класс Race соответствует принципам ___[SOLID][1]___, что способствует его гибкости, расширяемости и поддерживаемости.
***
## ___Class [RaceInformationManager](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/RaceInformationManager.java)___

___Class [RaceInformationManager](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/RaceInformationManager.java)___ находится в пакете com.zzerrgg. Он импортирует статические константы из `class Constants`.\
___Class RaceInformationManager___ содержит два метода: `carInformation` и `displayRaceInformation`.

Метод `carInformation` принимает два параметра: объект типа `Race` и строку типа `String`.
Он проверяет, равна ли данная строка константе `YOUR_CAR`. Если равно, то выводит строку `"Your Car"` и максимальную скорость, ускорение и уровень нитро автомобиля из объекта `Race`. 
Если строка не равна `YOUR_CAR`, то выводит строку `"Opponent Car"` и соответствующую информацию об автомобиле из объекта `Race`.

Метод `displayRaceInformation` принимает объект типа `Race` в качестве параметра. 
Он выводит строку `"Race Information"` и дистанцию гонки из объекта `Race`. 
Затем он вызывает метод `carInformation` дважды: один раз с константой `YOUR_CAR` и один раз с константой `OPPONENT_CAR`, чтобы отобразить информацию об автомобилях как игрока, так и оппонента.
В целом, `class RaceInformationManager` отвечает за отображение информации о гонке, включая информацию об автомобилях как игрока, так и оппонента.

Данный `class RaceInformationManager` соответствует принципу [SOLID][1] - ___Single Responsibility Principle___ (Принцип единственной ответственности).
Он отвечает только за управление информацией о гонке и несет ответственность за две основные функции: отображение информации о машине и отображение информации о гонке.
Метод `carInformation` отображает информацию о машине, принимая объект гонки и строку, указывающую, какую машину отобразить. 
Это отдельная ответственность, которая может быть выделена в отдельный класс или интерфейс, если потребуется расширение функциональности.
Метод `displayRaceInformation` отображает информацию о гонке, включая информацию о расстоянии и информацию о машинах. 
Опять же, это отдельная ответственность, которая может быть выделена в отдельный класс или интерфейс.

Таким образом, `class RaceInformationManager` соответствует принципу единственной ответственности, так как имеет только одну причину для изменения - изменение способа отображения информации о гонке или машинах.
***
## ___Class [RaceManager](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/RaceManager.java)___

___Class [RaceManager](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/RaceManager.java)___ отвечает за управление гонками. В нем определены методы для начала гонки, подготовки к гонке, изменения очков и расстояния, а также генерации автомобилей.\
Вот подробное описание каждого метода:
- `startRace(Race race)`: Этот метод запускает гонку. 
Он вызывает метод `preparingForTheRace` для подготовки к гонке, выводит сообщение о начале гонки, 
вызывает метод `logicOfTheRace` у объекта race для выполнения логики гонки, 
вызывает метод `changePointAndDistance` для изменения очков и расстояния автомобиля, выводит сообщение о завершении гонки и вызывает метод print у объекта `Menu`.


- `preparingForTheRace(Race race)`: Этот метод подготавливает гонку. 
Он генерирует случайный автомобиль с помощью метода `generateCar`, устанавливает расстояние гонки с помощью метода `generateInt`, 
и отображает информацию о гонке с помощью объекта `informationManager`.


- `changePointAndDistance(Car car, int points, int distance)`: Этот метод изменяет очки и расстояние автомобиля. 
Он увеличивает очки автомобиля на значение points и увеличивает пройденное расстояние автомобиля на значение `distance`.


- `generateCar()`: Этот метод генерирует случайный автомобиль.
Он генерирует случайные значения для максимальной скорости, ускорения и уровня нитро с помощью метода `generateInt`, и создает новый объект `Car` с этими значениями.


- `generateInt(int from, int to)`: Этот метод генерирует случайное целое число в заданном диапазоне. 
Он вычисляет разницу между `to` и `from`, генерирует случайное число в этом диапазоне с помощью объекта `random`, и возвращает результат.

___Class RaceManager___ соответствует принципам [SOLID][1], а именно:
- Принцип единственной ответственности ___(Single Responsibility Principle - SRP)___:\
___Class RaceManager___ отвечает только за управление гонкой и несет ответственность только за одну обязанность - запуск и управление гонкой. 
Он содержит методы для подготовки к гонке, изменения очков и расстояния, генерации автомобиля и чисел. Это позволяет классу быть легко понятным, изменяемым и тестируемым.


- Принцип открытости/закрытости ___(Open/Closed Principle - OCP)___:\
___Class RaceManager___ открыт для расширения (новые функции могут быть добавлены путем создания новых методов), но закрыт для изменения (существующий код не требует изменений при добавлении новых функций). 
Например, можно добавить новые методы для управления гонкой, не изменяя существующий код `class RaceManager`.


- Принцип подстановки Барбары Лисков ___(Liskov Substitution Principle - LSP)___:\
___Class RaceManager___ использует абстракцию `Race` для запуска гонки. Это означает, что любой подкласс, который наследует от `Race`, может быть использован вместо `Race` без изменения поведения `class RaceManager`. 
Например, если бы был создан подкласс `ElectricRace`, он мог бы быть использован вместо `Race` без изменения метода `startRace` в `class RaceManager`.


- Принцип разделения интерфейса ___(Interface Segregation Principle - ISP)___:\
___Class RaceManager___ не реализует интерфейсы, но он имеет только одну обязанность - управление гонкой. 
Это позволяет избежать зависимости от ненужных методов или интерфейсов, которые не используются в классе.


- Принцип инверсии зависимостей ___(Dependency Inversion Principle - DIP)___:\
___Class RaceManager___ зависит от абстракции `RaceInformationManager`, а не от конкретной реализации. 
Это позволяет легко заменить `RaceInformationManager` на другую реализацию без изменения кода `class RaceManager`.

В целом, `class RaceManager` соответствует принципам [SOLID][1], что делает его гибким, расширяемым и легко поддерживаемым.
***
## ___Class [Game](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Game.java)___

___Class [Game](https://github.com/Zerrgg/Race_Cars/blob/main/src/com/zzerrgg/Game.java)___ представляет игру и содержит методы для запуска и управления игрой.

В методе `start()` происходит инициализация игры, выводится приветственное сообщение, создается объект `Race` и `RaceManager`, 
а также выводится информация о машине игрока. Затем вызывается метод `Menu.print()` для отображения меню игры, 
и запускается метод `loop()`, который обрабатывает ввод пользователя и выполняет соответствующие действия в зависимости от выбранного пункта меню.

Метод `loop()` содержит бесконечный цикл, в котором считывается ввод пользователя с помощью объекта `Scanner`. 
Затем с помощью метода `Menu.getMenuByCod()` определяется выбранный пункт меню. 
Если выбранный пункт меню не существует, используется пункт меню по умолчанию. 
Затем с помощью оператора `switch` выполняются соответствующие действия в зависимости от выбранного пункта меню. 
Если выбран пункт меню `"START_RACE"`, вызывается метод `raceManager.startRace(race)`, 
если выбран пункт меню `"SHOW_STATISTICS"`, выводятся результаты гонки с помощью метода `race.printRaceResults()`, 
если выбран пункт меню `"STOP_GAME"`, выводится сообщение `"SEE_YOU"` и цикл завершается. 
Если выбран пункт меню по умолчанию или выбран несуществующий пункт меню, выводится заголовок пункта меню по умолчанию.

___Это основной класс игры, который управляет ее логикой и взаимодействием с пользователем.___

Данный `class Game` соответствует принципам [SOLID][1] следующим образом:
- Принцип единственной ответственности ___(Single Responsibility Principle)___:\
___Class Game___ отвечает только за управление игрой и несет ответственность только за одну функцию - запуск и управление игрой. 
Он не занимается непосредственно выполнением гонок или выводом статистики, а делегирует эти задачи другим классам (`RaceManager`, `RaceInformationManager`, `Menu`).


- Принцип открытости/закрытости ___(Open/Closed Principle)___:\
___Class Game___ закрыт для изменений, так как его основная функциональность уже реализована. 
Однако, он открыт для расширения, так как можно добавить новые функции или изменить поведение игры, не изменяя сам `class Game`.


- Принцип подстановки Барбары Лисков ___(Liskov Substitution Principle)___:\
___Class Game___ использует абстракции (`Race`, `RaceManager`, `RaceInformationManager`, `Menu`) вместо конкретных реализаций. 
Это позволяет подставлять различные реализации этих абстракций без изменения кода `class Game`.


- Принцип разделения интерфейса ___(Interface Segregation Principle)___:\
___Class Game___ не зависит от конкретных методов или свойств абстракций, которые он использует. 
Он взаимодействует только с общим интерфейсом, предоставляемым этими абстракциями.


- Принцип инверсии зависимостей ___(Dependency Inversion Principle)___:\
___Class Game___ зависит от абстракций (`Race`, `RaceManager`, `RaceInformationManager`, `Menu`), а не от конкретных реализаций. 
Это позволяет легко заменять или добавлять новые реализации этих абстракций без изменения `class Game`.
***
## ___Class [CarRaceApp](https://github.com/Zerrgg/Race_Cars/blob/main/src/CarRaceApp.java)___

___Class [CarRaceApp](https://github.com/Zerrgg/Race_Cars/blob/main/src/CarRaceApp.java)___ является точкой входа в приложение гонки автомобилей. 
Он содержит метод `main`, который является статическим и принимает массив строк `args` в качестве параметра.
Внутри метода `main` создается экземпляр `class Game` с именем `game`. Затем вызывается метод `start` на объекте `game`, чтобы начать игру.

[1]: https://github.com/IvanSavchuk/S.O.L.I.D.