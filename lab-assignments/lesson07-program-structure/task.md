
# Задача

Разработать программу опроса устройств ввода.

## Требования

1. Программа работает с устройствами ввода через библиотеку libevdev.

2. При запуске программа сканирует системные устройства ввода и отбирает кнопку
   выключения, мышь и клавиатуру. Остальные устройства ввода игнорируются. Тип
   устройства ввода определяется по типам и кодам генерируемых событий.

3. Программа мониторит очередь событий для каждого устройства и позволяет
   считать самое старое событие из очереди. После чтение событие удаляется. В
   зависимости от типа устройства очередь может быть организована в ядре или в
   самом приложении.

4. Для кнопки выключения программа запоминает нажатие кнопки, для мыши -
   нажатие левой и правой кнопки, для клавиатуры - нажатие цифр 0-9. Остальные
   события игнорируются.

5. Для каждого события от клавиатуры программа должна запоминать время нажатия
   клавиши (в произвольном формате).

6. Каждое устройство предоставляет обратный вызов (callback) для чтения
   события.

7. Каждое устройство представляется в программе двумя объектами: абстрактным
   объектом **struct device** и специальным объектом, определяемым типом
   устройства. Абстрактные объекты **struct device** хранятся в словаре
   **struct avl_tree** и содержат указатель на обратный вызов.

8. По команде **read \<device_name\>** программа выводит событие из указанного
   устройства (из всех для значения **all**). События читаются через обратный
   вызов (callback).

# Упрощенная задача

Исключить отслеживание событий от клавиатуры.
