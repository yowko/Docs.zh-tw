---
title: "了解使用 Override 和 New 關鍵字的時機 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 4888a93819b155d10b82bfd1ee105a73a1fdc126
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 了解使用 Override 和 New 關鍵字的時機 (C# 程式設計手冊)
在 C\# 中，衍生類別中的方法可以與基底類別中的方法同名。  您可以使用 [new](../../../csharp/language-reference/keywords/new.md) 和 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字來指定方法互動的方式。  `override` 修飾詞會「*擴充*」\(Extend\) 基底類別方法，而 `new` 修飾詞則加以「*隱藏*」\(Hide\)。  本主題中的範例會說明此差異。  
  
 在主控台應用程式中，宣告下列兩個類別：`BaseClass`和`DerivedClass`.  `DerivedClass` 繼承自 `BaseClass`。  
  
```c#  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
  
```  
  
 在`Main`方法中，宣告變數`bc`，`dc`，和`bcdc`.  
  
-   `bc` 屬於 `BaseClass`，而且其值的型別為 `BaseClass`。  
  
-   `dc` 屬於 `DerivedClass`，而且其值的型別為 `DerivedClass`。  
  
-   `bcdc` 屬於 `BaseClass`，而且其值的型別為 `DerivedClass`。  這是要注意的變數。  
  
 因為`bc`和`bcdc`具有類型`BaseClass`，除非您使用廣播，否則它們只能直接存取 `Method1`。  變數 `dc` 可以存取 `Method1` 和 `Method2`。  這些關聯性顯示在下列程式碼中。  
  
```c#  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
  
```  
  
 接下來，將下列 `Method2` 方法加入至 `BaseClass` 中。  此方法的簽章與 `DerivedClass` 中的 `Method2` 方法簽章相符。  
  
```c#  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
  
```  
  
 因為`BaseClass`現在有`Method2`方法，可以加入 `BaseClass`變數`bc`和`bcdc` 的第二個呼叫陳述式，如下列程式碼所示。  
  
```c#  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
  
```  
  
 當您產生專案時，您將看到，在 `BaseClass` 中加入 `Method2` 方法會產生警告。  警告表示，`DerivedClass` 中的 `Method2` 方法將 `Method2` 方法隱藏在 `BaseClass` 中。  如果想要產生這種結果，建議您使用 `Method2` 定義中的 `new` 關鍵字。  或者，您可以重新命名其中一個 `Method2`方法來解決警告，但這個方法並不實用。  
  
 加入 `new` 前，請執行程式以查看其他呼叫陳述式所產生的輸出。  將顯示下列結果。  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
  
```  
  
 `new` 關鍵字保留產生該輸出的關聯性，但會隱藏警告。  型別為 `BaseClass` 的變數會繼續存取 `BaseClass` 的成員，而型別為 `DerivedClass` 的變數則首先繼續存取 `DerivedClass` 的成員，然後再考慮繼承自 `BaseClass` 的成員。  
  
 若要隱藏此警告，請在 `DerivedClass` 中將 `new` 修飾詞加入至 `Method2` 的定義，如下列程式碼所示。  可在 `public` 之前或之後加入的修飾詞。  
  
```c#  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
  
```  
  
 再次執行程式以確認輸出沒有改變。  同時驗證不會再出現警告。  使用 `new` 就明確表示您知道它所修改的成員會隱藏繼承自基底類別的成員  如需關於透過繼承隱藏名稱的詳細資訊，請參閱[new 修飾詞](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 若要將這個行為與使用 `override` 的影響進行對比，請將下列方法加入至 `DerivedClass`。  可在 `public` 之前或之後加入的 `override` 修飾詞。  
  
```c#  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
  
```  
  
 將 `virtual` 修飾詞新增至`Method1` \(`BaseClass` 中\) 的定義。  可在 `public` 之前或之後加入的 `virtual` 修飾詞。  
  
```c#  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
  
```  
  
 再次執行專案。  請特別注意下列輸出的最後兩行。  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
  
```  
  
 使用 `override` 修飾詞可讓 `bcdc` 存取 `DerivedClass` 中定義的 `Method1` 方法。  這通常是在繼承階層架構中所需的行為。  您需要具有從衍生類別建立之值的物件，才能使用衍生類別中定義的方法。  您可以使用 `override` 擴充基底類別方法，達成該行為。  
  
 下列程式碼包含完整的範例。  
  
```c#  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
  
```  
  
 下列範例說明不同內容中的類似行為。  此範例定義了三個類別：名為 `Car` 的基底類別和兩個衍生自此基底類別的類別 `ConvertibleCar` 和 `Minivan`。  基底類別包含`DescribeCar`方法。  此方法會顯示汽車的基本描述，然後呼叫 `ShowDetails` 提供其他資訊。  三個類別中，每一個都定義一個`ShowDetails`方法。  `new` 修飾詞用於定義 `ConvertibleCar` 類別中的 `ShowDetails`。  `override` 修飾詞用於定義 `Minivan` 類別中的 `ShowDetails`。  
  
```c#  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
  
```  
  
 此範例測試 `ShowDetails` 呼叫的是哪個版本。  下列方法 `TestCars1` 會宣告每個類別的執行個體，然後呼叫每個執行個體上的 `DescribeCar`。  
  
```c#  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
  
```  
  
 `TestCars1`會產生下列輸出。  請特別注意 `car2` 的結果，可能不是您所預期的。  物件的型別是 `ConvertibleCar`，但 `DescribeCar` 不會存取定義於 `ConvertibleCar` 類別之 `ShowDetails` 的版本，因為該方法是使用 `new` 修飾詞而非 `override` 修飾詞所宣告。  因此，`ConvertibleCar`物件會顯示與 `Car`物件相同的描述。  與 `car3` \(這是 `Minivan` 物件\) 的結果進行比較。  在這種情況下，在 `Minivan` 類別中宣告的 `ShowDetails`方法會覆寫在 `Car` 類別中宣告的 `ShowDetails`方法，所顯示的描述說明小型貨車。  
  
```c#  
  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 `TestCars2` 會建立具有型別 `Car` 的物件清單。  物件的值是從 `Car`、`ConvertibleCar` 和 `Minivan` 類別具現化而來。  在清單的每個項目呼叫 `DescribeCar`。  下列程式碼顯示 `TestCars2` 的定義。  
  
```c#  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
  
```  
  
 將顯示以下輸出。  請注意，這與 `TestCars1` 所顯示的輸出相同。  不論物件的型別是 `TestCars1` 中的 `ConvertibleCar`，還是 `TestCars2` 中的 `Car`，都不會呼叫 `ConvertibleCar` 類別的 `ShowDetails` 方法。  相反的，無論 `car3` 的型別是 `Minivan` 還是 `Car`，它在這兩種情況下都會呼叫 `Minivan` 類別中的 `ShowDetails` 方法。  
  
```c#  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 下列範例使用了 `TestCars3` 和 `TestCars4` 方法。  這些方法會先從型別宣告為 `ConvertibleCar` 和 `Minivan` \(`TestCars3`\) 的物件，然後再從型別宣告為 `Car` \(`TestCars4`\) 的物件直接呼叫 `ShowDetails`。  下列程式碼會定義這兩個方法。  
  
```c#  
  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
```  
  
 此方法會產生下列輸出，這對應至本主題中第一個範例的結果。  
  
```c#  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
  
```  
  
 下列程式碼顯示完整的專案及其輸出。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
  
```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [使用 Override 和 New 關鍵字的進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)