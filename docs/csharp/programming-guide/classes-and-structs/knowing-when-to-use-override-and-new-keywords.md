---
title: "了解使用 Override 和 New 關鍵字的時機 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b4d53f16f046839d56bc1dc37f7b2d8816c5956f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>了解使用 Override 和 New 關鍵字的時機 (C# 程式設計手冊)
在 C# 中，衍生類別的方法名稱可以與基底類別的方法名稱相同。 您可以使用 [new](../../../csharp/language-reference/keywords/new.md) 和 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字來指定方法的互動方式。 `override` 修飾詞可「擴充」基底類別方法，而 `new` 修飾詞會「隱藏」基底類別方法。 本主題的範例會說明其間的差異。  
  
 在主控台應用程式中，宣告 `BaseClass` 和 `DerivedClass` 這兩個類別。 `DerivedClass` 繼承自 `BaseClass`。  
  
```csharp  
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
  
 在 `Main` 方法中，宣告 `bc`、`dc` 和 `bcdc` 變數。  
  
-   `bc` 屬於 `BaseClass` 類型，而其值為 `BaseClass` 類型。  
  
-   `dc` 屬於 `DerivedClass` 類型，而其值為 `DerivedClass` 類型。  
  
-   `bcdc` 屬於 `BaseClass` 類型，而其值為 `DerivedClass` 類型。 這是值得注意的變數。  
  
 由於 `bc` 和 `bcdc` 具有 `BaseClass` 類型，因此只能直接存取 `Method1` (除非您使用轉型)。 `dc` 變數可以同時存取 `Method1` 和 `Method2`。 下列程式碼顯示這些關聯性。  
  
```csharp  
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
  
 接下來，將下列 `Method2` 方法新增至 `BaseClass`。 此方法的簽章與 `DerivedClass` 的 `Method2` 方法簽章相符。  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 由於 `BaseClass` 現已具備 `Method2` 方法，因此您可以為 `BaseClass` 的 `bc` 和 `bcdc` 變數新增第二個呼叫陳述式，如下列程式碼所示。  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 在建置專案時，您會發現在新增 `BaseClass` 的 `Method2` 方法時會產生警告。 警告指出，`DerivedClass` 的 `Method2` 方法會隱藏 `BaseClass` 的 `Method2` 方法。 如果您想要這種結果，建議您在 `Method2` 定義中使用 `new` 關鍵字。 或者，您可以重新命名其中一個 `Method2` 方法來解決警告，但不一定總是可行。  
  
 請先執行程式並查看其他呼叫陳述式所產生的輸出，之後再加入 `new`。 即會顯示下列結果。  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` 關鍵字會保留產生該輸出的關聯性，但是它會隱藏警告。 如果變數具有 `BaseClass` 類型，其會繼續存取 `BaseClass` 的成員，而含 `DerivedClass` 類型的變數則會繼續優先存取 `DerivedClass` 中的成員，然後才考慮繼承自 `BaseClass` 的成員。  
  
 若要隱藏警告，請將 `new` 修飾詞新增至 `DerivedClass` 中的 `Method2` 定義，如下列程式碼所示。 您可在 `public` 之前或之後的位置新增修飾詞。  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 再次執行程式，確認輸出尚未變更， 另請確認警告已不再顯示。 使用 `new` 時，即表示您了解此關鍵字所修改的成員，會隱藏繼承自基底類別的成員。 如需透過繼承隱藏名稱的詳細資訊，請參閱 [new 修飾詞](../../../csharp/language-reference/keywords/new-modifier.md)。  
  
 若要比較這項行為與使用 `override` 的效果，請將下列方法新增至 `DerivedClass`。 您可在 `public` 之前或之後的位置新增 `override` 修飾詞。  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 請將 `virtual` 修飾詞新增至 `BaseClass` 的 `Method1` 定義。 您可在 `public` 之前或之後的位置新增 `virtual` 修飾詞。  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 重新執行專案。 請特別注意下列輸出的最後兩行。  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 使用 `override` 修飾詞時，可讓 `bcdc` 存取 `DerivedClass` 中所定義的 `Method1` 方法。 一般而言，這是繼承階層架構所要的結果。 您希望物件的值都是從衍生類別所建立，以使用衍生類別中定義的方法。 您可以使用 `override` 來擴充基底類別方法，進而實現這種結果。  
  
 下列程式碼包含完整的範例。  
  
```csharp  
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
  
 下列範例說明不同內容中的類似行為。 此範例會定義下列三個類別：名為 `Car` 的基底類別，以及兩個由此衍生的 `ConvertibleCar` 和 `Minivan` 類別。 基底類別包含 `DescribeCar` 方法。 此方法會顯示車輛的基本描述，然後呼叫 `ShowDetails` 來提供其他資訊。 這三個類別都會定義 `ShowDetails` 方法。 `new` 修飾詞可用來定義 `ConvertibleCar` 類別中的 `ShowDetails`。 `override` 修飾詞可用來定義 `Minivan` 類別中的 `ShowDetails`。  
  
```csharp  
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
  
 此範例會測試哪個版本的 `ShowDetails` 受到呼叫。 下列 `TestCars1` 方法會宣告每個類別的執行個體，然後呼叫每個執行個體上的 `DescribeCar`。  
  
```csharp  
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
  
 `TestCars1` 會產生下列輸出。 請特別注意，`car2` 的結果可能與您所預期的不同。 物件的類型是 `ConvertibleCar`，但 `DescribeCar` 不會存取 `ConvertibleCar` 類別中所定義的 `ShowDetails` 版本，因為該方法是使用 `new` 修飾詞來進行宣告，而不是 `override` 修飾詞。 如此一來，`ConvertibleCar` 物件顯示的描述會與 `Car` 物件相同。 `car3` (也就是 `Minivan` 物件) 的結果則相反。 在此情況下，`Minivan` 類別中所宣告的 `ShowDetails` 方法會覆寫 `Car` 類別中所宣告的 `ShowDetails` 方法，而且顯示的描述為休旅車。  
  
```csharp  
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
  
 `TestCars2` 會建立具有 `Car` 類型的物件清單。 物件的值是從 `Car`、`ConvertibleCar` 和 `Minivan` 類別具現化而得。 清單上的每個項目都會呼叫 `DescribeCar`。 下列程式碼顯示 `TestCars2` 的定義。  
  
```csharp  
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
  
 隨即顯示下列輸出。 請注意，此輸出與 `TestCars1` 顯示的輸出相同。 不論物件的類型是 `ConvertibleCar` (如 `TestCars1` 中)，或 `Car` (如 `TestCars2` 中)，系統均不會呼叫 `ConvertibleCar` 類別的 `ShowDetails` 方法。 相反地，`car3` 會從 `Minivan` 呼叫這兩種類別的 `ShowDetails` 方法，不論其為 `Minivan` 類型或 `Car` 類型。  
  
```csharp  
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
  
 `TestCars3` 和 `TestCars4` 方法會完成範例。 這些方法會先從宣告為具有 `ConvertibleCar` 和 `Minivan` 類型的物件 (`TestCars3`)，再從物件宣告為具有 `Car` 類型的物件 (`TestCars4`) 直接呼叫 `ShowDetails`。 下列程式碼會定義這兩種方法。  
  
```csharp  
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
  
 這些方法會產生下列輸出，並與本主題中的第一個範例結果對應。  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 下列程式碼顯示完整專案和其輸出。  
  
```csharp  
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
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [使用 Override 和 New 關鍵字進行版本控制](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [base](../../../csharp/language-reference/keywords/base.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)
