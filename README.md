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
#### 3 Создается переменная Integer ii = 2 в памяти стека фрейма main() (т.к. в интервале -128 -- 127)
#### 4 В стеке создается фрейм памяти для метода printAll() и в нем ссылка о на объект Object, созданный в heap п.п. 2 и переменные int i и ii.
#### 5 В heap выделяется блок памяти под Integer, а в памяти стека фрейма printAll() создается ссылка на него uselessVar.
#### 6 В стеке создается фрейм памяти для метода println() и в нем переменные int i и ii и ссылка на строку, которую вернет метод toString(). В heap под эту строку выделяется память в String Pool. 
#### В стеке создается фрейм памяти для метода toString() и в нем ссылка о на объект Object, созданный в heap п.п. 2
#### 7 В стеке создается фрейм памяти для метода println() и в нем ссылка на строку "finished", сама строка попадает в String Pool.
#### Сборщик мусора сначала удалит неиспользуемую переменную uselessVar, строку из String Pool после выполнения метода println() п.6, Object, строку из String Pool после выполнения метода println() п.7

![image](https://user-images.githubusercontent.com/94550891/152858760-92741bfa-e026-447d-8f04-0f1ca32c934b.png)

### Сомнения! Под каждый метод создается фрейм памяти в стеке. Стек работает сверху вниз. По логике, верхний println() должен находиться между main() и printAll(). Тогда все по порядку: toString() возвращает строку, фрейм закрывается; println() печатает строку и i, ii, фрейм закрывается; фрейм printAll() закрывается; println() печатает строку "finished", фрейм закрывается, фрейм main() закрывается. ???? 
