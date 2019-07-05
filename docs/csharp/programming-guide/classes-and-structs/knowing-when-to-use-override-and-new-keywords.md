---
title: 了解使用 Override 和 New 關鍵字的時機 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: eae57ae1f285e7f0e44c49e3d54fbd81bb4be591
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398434"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="fa6e7-102">了解使用 Override 和 New 關鍵字的時機 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="fa6e7-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="fa6e7-103">在 C# 中，衍生類別的方法名稱可以與基底類別的方法名稱相同。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="fa6e7-104">您可以使用 [new](../../../csharp/language-reference/keywords/new-modifier.md) 和 [override](../../../csharp/language-reference/keywords/override.md) 關鍵字來指定方法的互動方式。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new-modifier.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="fa6e7-105">`override` 修飾詞會「延伸」  基底類別的 `virtual` 方法，`new` 修飾詞則會「隱藏」  可存取的基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-105">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="fa6e7-106">本主題的範例會說明其間的差異。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="fa6e7-107">在主控台應用程式中，宣告 `BaseClass` 和 `DerivedClass` 這兩個類別。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="fa6e7-108">`DerivedClass` 繼承自 `BaseClass`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-109">在 `Main` 方法中，宣告 `bc`、`dc` 和 `bcdc` 變數。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="fa6e7-110">`bc` 屬於 `BaseClass` 類型，而其值為 `BaseClass` 類型。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="fa6e7-111">`dc` 屬於 `DerivedClass` 類型，而其值為 `DerivedClass` 類型。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="fa6e7-112">`bcdc` 屬於 `BaseClass` 類型，而其值為 `DerivedClass` 類型。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="fa6e7-113">這是值得注意的變數。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="fa6e7-114">由於 `bc` 和 `bcdc` 具有 `BaseClass` 類型，因此只能直接存取 `Method1` (除非您使用轉型)。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="fa6e7-115">`dc` 變數可以同時存取 `Method1` 和 `Method2`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="fa6e7-116">下列程式碼顯示這些關聯性。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-117">接下來，將下列 `Method2` 方法新增至 `BaseClass`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="fa6e7-118">此方法的簽章與 `DerivedClass` 的 `Method2` 方法簽章相符。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="fa6e7-119">由於 `BaseClass` 現已具備 `Method2` 方法，因此您可以為 `BaseClass` 的 `bc` 和 `bcdc` 變數新增第二個呼叫陳述式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="fa6e7-120">在建置專案時，您會發現在新增 `BaseClass` 的 `Method2` 方法時會產生警告。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="fa6e7-121">警告指出，`DerivedClass` 的 `Method2` 方法會隱藏 `BaseClass` 的 `Method2` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="fa6e7-122">如果您想要這種結果，建議您在 `Method2` 定義中使用 `new` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="fa6e7-123">或者，您可以重新命名其中一個 `Method2` 方法來解決警告，但不一定總是可行。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="fa6e7-124">請先執行程式並查看其他呼叫陳述式所產生的輸出，之後再加入 `new`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="fa6e7-125">即會顯示下列結果。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="fa6e7-126">`new` 關鍵字會保留產生該輸出的關聯性，但是它會隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="fa6e7-127">如果變數具有 `BaseClass` 類型，其會繼續存取 `BaseClass` 的成員，而含 `DerivedClass` 類型的變數則會繼續優先存取 `DerivedClass` 中的成員，然後才考慮繼承自 `BaseClass` 的成員。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="fa6e7-128">若要隱藏警告，請將 `new` 修飾詞新增至 `DerivedClass` 中的 `Method2` 定義，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="fa6e7-129">您可在 `public` 之前或之後的位置新增修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="fa6e7-130">再次執行程式，確認輸出尚未變更，</span><span class="sxs-lookup"><span data-stu-id="fa6e7-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="fa6e7-131">另請確認警告已不再顯示。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="fa6e7-132">使用 `new` 時，即表示您了解此關鍵字所修改的成員，會隱藏繼承自基底類別的成員。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="fa6e7-133">如需透過繼承隱藏名稱的詳細資訊，請參閱 [new 修飾詞](../../../csharp/language-reference/keywords/new-modifier.md)。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="fa6e7-134">若要比較這項行為與使用 `override` 的效果，請將下列方法新增至 `DerivedClass`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="fa6e7-135">您可在 `public` 之前或之後的位置新增 `override` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="fa6e7-136">請將 `virtual` 修飾詞新增至 `BaseClass` 的 `Method1` 定義。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="fa6e7-137">您可在 `public` 之前或之後的位置新增 `virtual` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="fa6e7-138">重新執行專案。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-138">Run the project again.</span></span> <span data-ttu-id="fa6e7-139">請特別注意下列輸出的最後兩行。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="fa6e7-140">使用 `override` 修飾詞時，可讓 `bcdc` 存取 `DerivedClass` 中所定義的 `Method1` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="fa6e7-141">一般而言，這是繼承階層架構所要的結果。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="fa6e7-142">您希望物件的值都是從衍生類別所建立，以使用衍生類別中定義的方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="fa6e7-143">您可以使用 `override` 來擴充基底類別方法，進而實現這種結果。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="fa6e7-144">下列程式碼包含完整的範例。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-145">下列範例說明不同內容中的類似行為。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="fa6e7-146">此範例會定義下列三個類別：名為 `Car` 的基底類別，以及兩個由此衍生的 `ConvertibleCar` 和 `Minivan` 類別。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="fa6e7-147">基底類別包含 `DescribeCar` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="fa6e7-148">此方法會顯示車輛的基本描述，然後呼叫 `ShowDetails` 來提供其他資訊。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="fa6e7-149">這三個類別都會定義 `ShowDetails` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="fa6e7-150">`new` 修飾詞可用來定義 `ConvertibleCar` 類別中的 `ShowDetails`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="fa6e7-151">`override` 修飾詞可用來定義 `Minivan` 類別中的 `ShowDetails`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-152">此範例會測試哪個版本的 `ShowDetails` 受到呼叫。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="fa6e7-153">下列 `TestCars1` 方法會宣告每個類別的執行個體，然後呼叫每個執行個體上的 `DescribeCar`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-154">`TestCars1` 會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="fa6e7-155">請特別注意，`car2` 的結果可能與您所預期的不同。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="fa6e7-156">物件的類型是 `ConvertibleCar`，但 `DescribeCar` 不會存取 `ConvertibleCar` 類別中所定義的 `ShowDetails` 版本，因為該方法是使用 `new` 修飾詞來進行宣告，而不是 `override` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="fa6e7-157">如此一來，`ConvertibleCar` 物件顯示的描述會與 `Car` 物件相同。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="fa6e7-158">`car3` (也就是 `Minivan` 物件) 的結果則相反。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="fa6e7-159">在此情況下，`Minivan` 類別中所宣告的 `ShowDetails` 方法會覆寫 `Car` 類別中所宣告的 `ShowDetails` 方法，而且顯示的描述為休旅車。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-160">`TestCars2` 會建立具有 `Car` 類型的物件清單。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="fa6e7-161">物件的值是從 `Car`、`ConvertibleCar` 和 `Minivan` 類別具現化而得。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="fa6e7-162">清單上的每個項目都會呼叫 `DescribeCar`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="fa6e7-163">下列程式碼顯示 `TestCars2` 的定義。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-164">隨即顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-164">The following output is displayed.</span></span> <span data-ttu-id="fa6e7-165">請注意，此輸出與 `TestCars1` 顯示的輸出相同。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="fa6e7-166">不論物件的類型是 `ConvertibleCar` (如 `TestCars1` 中)，或 `Car` (如 `TestCars2` 中)，系統均不會呼叫 `ConvertibleCar` 類別的 `ShowDetails` 方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="fa6e7-167">相反地，`car3` 會從 `Minivan` 呼叫這兩種類別的 `ShowDetails` 方法，不論其為 `Minivan` 類型或 `Car` 類型。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-168">`TestCars3` 和 `TestCars4` 方法會完成範例。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="fa6e7-169">這些方法會先從宣告為具有 `ConvertibleCar` 和 `Minivan` 類型的物件 (`TestCars3`)，再從物件宣告為具有 `Car` 類型的物件 (`TestCars4`) 直接呼叫 `ShowDetails`。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="fa6e7-170">下列程式碼會定義這兩種方法。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-171">這些方法會產生下列輸出，並與本主題中的第一個範例結果對應。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="fa6e7-172">下列程式碼顯示完整專案和其輸出。</span><span class="sxs-lookup"><span data-stu-id="fa6e7-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa6e7-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa6e7-173">See also</span></span>

- [<span data-ttu-id="fa6e7-174">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fa6e7-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="fa6e7-175">類別和結構</span><span class="sxs-lookup"><span data-stu-id="fa6e7-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="fa6e7-176">使用 Override 和 New 關鍵字進行版本控制</span><span class="sxs-lookup"><span data-stu-id="fa6e7-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="fa6e7-177">base</span><span class="sxs-lookup"><span data-stu-id="fa6e7-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="fa6e7-178">abstract</span><span class="sxs-lookup"><span data-stu-id="fa6e7-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)
