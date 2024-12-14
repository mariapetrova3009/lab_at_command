# Лабораторная работа: Создание и выполнение запланированной задачи с использованием команды `at`

# Пример

Команда `at` в Linux используется для планирования выполнения одноразовой задачи в определенное время в будущем. Она позволяет указать конкретное время выполнения команды или скрипта.

### Установка

Для установки команды `at` выполните следующую команду в терминале:

```bash
sudo apt install at
```

### Запуск службы

После установки служба `atd` должна запуститься автоматически. Если она не запущена, ее можно запустить и включить с помощью следующих команд:

```bash
sudo systemctl start atd
sudo systemctl enable atd
```

### Использование команды `at`

При выполнении команды `at` открывается интерактивное приглашение, в котором можно ввести команды, которые необходимо выполнить в указанное время. Например:

```bash
at 2:37 PM
```

После этого вы можете ввести команды, которые нужно выполнить. Например:

```bash
echo "Hello, World" > /example/hello.txt
```

Чтобы сохранить запланированное задание и выйти из интерактивного окна, нажмите `Ctrl+D`.

Если вы хотите отменить задание до его сохранения, используйте `Ctrl+C`.

Ниже показан пример использования команды `at`:

```bash
at 2:37 PM
echo "Hello, World!" > /example/hello.txt
<Ctrl+D>
```

После выполнения в указанное время файл `/example/hello.txt` будет создан с содержимым `Hello, World!`.

# Задание

# Использование команды `at` в Linux

Команда `at` в Linux используется для планирования выполнения одноразовой задачи в определенное время в будущем. Она позволяет указать конкретное время выполнения команды или скрипта.

## Установка

Для установки команды `at` выполните следующую команду в терминале:

```bash
sudo apt install at
```

## Запуск службы

После установки служба `atd` должна запуститься автоматически. Если она не запущена, ее можно запустить и включить с помощью следующих команд:

```bash
sudo systemctl start atd
sudo systemctl enable atd
```



### Задание

#### Создайте текстовый файл с именем `input.txt
1. Добавьте в файл текст
   ```bash
   echo "This is the input file for the at task." > input.txt
   ```

2. Напишите скрипт `process_script.sh`, который выполняет следующие действия:
   - Читает содержимое файла `input.txt`.
   - Создаёт новый файл `output.txt` с добавлением текущей даты и времени.

   Содержимое скрипта:
   ```bash
   cat << EOF > process_script.sh
   #!/bin/bash
   echo "Processing input file..." > output.txt
   cat input.txt >> output.txt
   echo "Task completed at: $(date)" >> output.txt
   EOF
   ```

3. Сделайте скрипт исполняемым:
   ```bash
   chmod +x process_script.sh
   ```

#### Этап 2: Запланируйте выполнение скрипта
1. Используйте команду `at`, чтобы запланировать выполнение скрипта через 1 минуту:
   ```bash
   at now + 1 minutes -f ./process_script.sh
   ```

2. Убедитесь, что задача запланирована, с помощью команды:
   ```bash
   atq
   ```

#### Этап 3: Управление задачами
1. Предварительно проверьте содержимое запланированной задачи:
   ```bash
   at -c 1
   ```

2. Удалите задачу (при необходимости):
   ```bash
   atrm 1
   ```

#### Этап 4: Проверка выполнения
1. Дождитесь выполнения задачи. Проверьте, создан ли файл `output.txt`, и убедитесь, что его содержимое корректно.
   Пример проверки:
   ```bash
   cat output.txt
   ```
#### Этап 5: Создание нового задания с указанием даты и времени
1. Запланируйте выполнение другой команды с указанием конкретной даты и времени. Например:
   ```bash
   at 01:47PM 2023-08-09
   echo "This is a scheduled task with specific time." > /tmp/specific_task.txt
   <Ctrl+D>
   ```
2. Проверьте выполнение этой задачи в указанное время, убедившись, что файл `/tmp/specific_task.txt` создан.




