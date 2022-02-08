# jvm-task1

public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}

#### Подсистема загрузчиков классов ClassLoaders загружает класс JvmComprehension, проводит проверку валидности, подготовку примитивов в статистических полях, связывание ссылок на другие классы, static - инициализацию и мета-информация о классе помещается в область памяти Metaspace. 
#### Java Runtime создает стековую память для использования методом main()
#### 1 Создается переменная int i = 1 в памяти стека фрейма main()
#### 2 В heap выделяется блок памяти Object, а в памяти стека фрейма main() создается ссылка на него о.
#### 3 Создается ссылка ii в памяти стека фрейма main() на переменную Integer, значение которой = 2  помещается в heap.
#### 4 В стеке создается фрейм памяти для метода printAll() и в нем ссылка о на объект Object, созданный в heap п. 2, ссылка ii на объект Integer, созданный в heap п.3 и переменная int i.
#### 5 В heap выделяется блок памяти под Integer, а в памяти стека фрейма printAll() создается ссылка на него uselessVar.
#### 6 В стеке создается фрейм памяти для метода println() и в нем переменная int i, ссылка ii объект Integer, созданный в heap п.3, ссылка на ссылка на строку, которую вернет метод toString(). В heap под эту строку выделяется память в String Pool. 
#### В стеке создается фрейм памяти для метода toString() и в нем ссылка о на объект Object, созданный в heap п.п. 2. Метод toString() возвращает строку, фрейм закрывается. Метод println() выводит на печать, фрейм закрывается. Метод printAll() отработал, фрейм закрывается. 
#### 7 Рисунок 2. В стеке создается фрейм памяти для метода println() и в нем ссылка на строку "finished", сама строка попадает в String Pool. Строка выводится на печать, закрывается фрейм метода println(). Закрывается фрейм метода main(). 
#### Сборщик мусора сначала удалит неиспользуемую переменную uselessVar, строку из String Pool после выполнения метода println() п.6, Object, строку из String Pool после выполнения метода println() п.7

![image](https://user-images.githubusercontent.com/94550891/153047972-d6e75ecf-52e7-41e9-a0db-1cc541990ca4.png)

![image](https://user-images.githubusercontent.com/94550891/153048036-2a03b8d0-a18a-46b5-a154-a45144052483.png)

