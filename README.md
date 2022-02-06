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
#### 3 В heap выделяется блок памяти под Integer, а в памяти стека фрейма main() создается ссылка на него ii.
#### 4 В стеке создается фрейм памяти для метода printAll() и в нем ссылки о и ii  на объекты Object и Integer, созданные в heap п.п. 2,3 и переменная int i.
#### 5 В heap выделяется блок памяти под Integer, а в памяти стека фрейма printAll() создается ссылка на него uselessVar.









 
  
  
  
  
 
 
  
  
 
 
  
  
  
 
 
  
 



 
