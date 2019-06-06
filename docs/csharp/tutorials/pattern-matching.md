---
title: 使用模式比對功能來擴充資料類型
description: 此進階教學課程示範如何使用模式比對技術，以個別建立的資料和演算法來建立功能。
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 58e4a9175752c7845507f48a3684747092dc609a
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378074"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="15fb5-103">教學課程：使用模式比對功能來擴充資料類型</span><span class="sxs-lookup"><span data-stu-id="15fb5-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="15fb5-104">C# 7 引進基本的模式比對功能。</span><span class="sxs-lookup"><span data-stu-id="15fb5-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="15fb5-105">那些功能已在 C# 8 中擴充，有了新的運算式和模式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="15fb5-106">您可以撰寫行為如同您擴充其他程式庫中之型別的功能。</span><span class="sxs-lookup"><span data-stu-id="15fb5-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="15fb5-107">模式的另一個用途是建立應用程式需要的功能，但該功能不是要擴充之型別的基本功能。</span><span class="sxs-lookup"><span data-stu-id="15fb5-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="15fb5-108">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="15fb5-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="15fb5-109">辨識應該使用模式比對的情況。</span><span class="sxs-lookup"><span data-stu-id="15fb5-109">Recognize situations where pattern matching should be used.</span></span>
> * <span data-ttu-id="15fb5-110">使用模式比對運算式根據類型和屬性值實作行為。</span><span class="sxs-lookup"><span data-stu-id="15fb5-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> * <span data-ttu-id="15fb5-111">結合模式比對與其他技術，建立完整的演算法。</span><span class="sxs-lookup"><span data-stu-id="15fb5-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="15fb5-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="15fb5-112">Prerequisites</span></span>

<span data-ttu-id="15fb5-113">您將需要設定您的機器，以執行 .NET Core (包括 C# 8.0 預覽版編譯器)。</span><span class="sxs-lookup"><span data-stu-id="15fb5-113">You'll need to set up your machine to run .NET Core, including the C# 8.0 preview compiler.</span></span> <span data-ttu-id="15fb5-114">您可以在最新的 [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) (或最新的 [.NET Core 3.0 Preview](https://dotnet.microsoft.com/download/dotnet-core/3.0)) 取得 C# 8 預覽版編譯器。</span><span class="sxs-lookup"><span data-stu-id="15fb5-114">The C# 8 preview compiler is available with the latest [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the latest [.NET Core 3.0 preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="15fb5-115">本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="15fb5-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="15fb5-116">模式比對的案例</span><span class="sxs-lookup"><span data-stu-id="15fb5-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="15fb5-117">新式開發通常包括整合來自多個來源的資料，並在單一且一致的應用程式內呈現來自該資料的資訊和見解。</span><span class="sxs-lookup"><span data-stu-id="15fb5-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="15fb5-118">您和您的小組不會有代表傳入資料之所有型別的控制權和存取權。</span><span class="sxs-lookup"><span data-stu-id="15fb5-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="15fb5-119">傳統物件導向設計要求您在您的應用程式中建立型別，以代表來自多個資料來源的每個資料類型。</span><span class="sxs-lookup"><span data-stu-id="15fb5-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="15fb5-120">然後，您的應用程式會使用這些新型別、建立繼承階層、建立虛擬方法，以及實作抽象概念。</span><span class="sxs-lookup"><span data-stu-id="15fb5-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="15fb5-121">那些技術可以運作，而且有時候它們是最好的工具。</span><span class="sxs-lookup"><span data-stu-id="15fb5-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="15fb5-122">其他時候，您可以撰寫少一點程式碼。</span><span class="sxs-lookup"><span data-stu-id="15fb5-122">Other times you can write less code.</span></span> <span data-ttu-id="15fb5-123">透過使用將資料與操作該資料之作業分離的技術，您可以撰寫更清楚的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15fb5-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="15fb5-124">在此教學課程中，您會建立並探索在單一情況下，接受來自數個外部來源之資料的應用程式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="15fb5-125">您會了解**模式比對**如何提供有效率的方法，以不屬於原始系統的方式來取用及處理該資料。</span><span class="sxs-lookup"><span data-stu-id="15fb5-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="15fb5-126">請考慮使用通行費和尖峰時段計費來管理交通的主要都會區。</span><span class="sxs-lookup"><span data-stu-id="15fb5-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="15fb5-127">您要撰寫根據車輛類型計算其通行費的應用程式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="15fb5-128">之後的改進會併入根據車輛中乘客數目的計費。</span><span class="sxs-lookup"><span data-stu-id="15fb5-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="15fb5-129">進一步的改進會新增根據時間和星期幾的計費。</span><span class="sxs-lookup"><span data-stu-id="15fb5-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="15fb5-130">從這個簡短描述，您可能已經快速地勾勒出建構此系統模型的階層。</span><span class="sxs-lookup"><span data-stu-id="15fb5-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="15fb5-131">不過，您的資料來自多個來源，如其他車輛註冊管理系統。</span><span class="sxs-lookup"><span data-stu-id="15fb5-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="15fb5-132">這些系統提供建構資料模型的不同類別，而且您沒有任何可用的單一物件模型。</span><span class="sxs-lookup"><span data-stu-id="15fb5-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="15fb5-133">在此教學課程中，您將使用這些簡化的類別，從來自外部系統的這些車輛資料建構模型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="15fb5-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="15fb5-134">您可以從 [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub 存放庫下載起始程式碼。</span><span class="sxs-lookup"><span data-stu-id="15fb5-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="15fb5-135">您可以看到車輛類別是來自不同的系統，且位於不同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="15fb5-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="15fb5-136">除了可用的 `System.Object` 之外，沒有通用的基底類別。</span><span class="sxs-lookup"><span data-stu-id="15fb5-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="15fb5-137">模式比對設計</span><span class="sxs-lookup"><span data-stu-id="15fb5-137">Pattern matching designs</span></span>

<span data-ttu-id="15fb5-138">本教學課程所使用案例會醒目提示適合以模式比對來解決的問題類型：</span><span class="sxs-lookup"><span data-stu-id="15fb5-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="15fb5-139">您要處理的物件不在符合您目標的物件階層中。</span><span class="sxs-lookup"><span data-stu-id="15fb5-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="15fb5-140">您可能會使用屬於不相關之系統的類別。</span><span class="sxs-lookup"><span data-stu-id="15fb5-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="15fb5-141">您要新增的功能不屬於這些類別的核心抽象概念。</span><span class="sxs-lookup"><span data-stu-id="15fb5-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="15fb5-142">車輛付的通行費隨不同類型的車輛而「變更」，但通行費不是車輛的核心函式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="15fb5-143">當資料的「圖形」與資料上的「作業」不是一起描述時，C# 中的模式比對功能可讓它變得更容易使用。</span><span class="sxs-lookup"><span data-stu-id="15fb5-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="15fb5-144">實作基本通行費計算</span><span class="sxs-lookup"><span data-stu-id="15fb5-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="15fb5-145">最基本的通行費計算僅依賴車輛類型：</span><span class="sxs-lookup"><span data-stu-id="15fb5-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="15fb5-146">`Car` 是 $2.00。</span><span class="sxs-lookup"><span data-stu-id="15fb5-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="15fb5-147">`Taxi` 是 $3.50。</span><span class="sxs-lookup"><span data-stu-id="15fb5-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="15fb5-148">`Bus` 是 $5.00。</span><span class="sxs-lookup"><span data-stu-id="15fb5-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="15fb5-149">`DeliveryTruck` 是 $10.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="15fb5-150">建立新的 `TollCalculator` 類別，並在車輛類型上實作模式比對來取得通行費金額。</span><span class="sxs-lookup"><span data-stu-id="15fb5-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="15fb5-151">下列程式碼示範 `TollCalculator` 的初始實作。</span><span class="sxs-lookup"><span data-stu-id="15fb5-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="15fb5-152">上述程式碼使用可測試**型別模式**的 **switch 運算式** (與 [`switch`](../language-reference/keywords/switch.md) 陳述式不同)。</span><span class="sxs-lookup"><span data-stu-id="15fb5-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="15fb5-153">**switch 運算式**的開始是變數 (上述程式碼中的 `vehicle`)，接著是 `switch` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="15fb5-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="15fb5-154">然後所有的 **switch 臂**都在大括號內。</span><span class="sxs-lookup"><span data-stu-id="15fb5-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="15fb5-155">`switch` 運算式會對括住 `switch` 陳述式的語法進行其他細分。</span><span class="sxs-lookup"><span data-stu-id="15fb5-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="15fb5-156">已省略 `case` 關鍵字，且每個臂的結果都是運算式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="15fb5-157">最後兩個臂顯示新的語言功能。</span><span class="sxs-lookup"><span data-stu-id="15fb5-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="15fb5-158">`{ }` 案例比對不符合先前臂的任何非 Null 物件。</span><span class="sxs-lookup"><span data-stu-id="15fb5-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="15fb5-159">此臂會攔截傳遞到此方法的任何不正確型別。</span><span class="sxs-lookup"><span data-stu-id="15fb5-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="15fb5-160">`{ }` 案例必須遵循每種車輛類型的案例。</span><span class="sxs-lookup"><span data-stu-id="15fb5-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="15fb5-161">順序如已顛倒，則 `{ }` 案例會優先。</span><span class="sxs-lookup"><span data-stu-id="15fb5-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="15fb5-162">最後，`null` 模式會偵測 `null` 於何時傳遞至這個方法。</span><span class="sxs-lookup"><span data-stu-id="15fb5-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="15fb5-163">因為其他型別模式只比對正確型別的非 Null 物件，所以 `null` 可以在最後。</span><span class="sxs-lookup"><span data-stu-id="15fb5-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="15fb5-164">您可以使用 `Program.cs` 中的下列程式碼來測試此程式碼：</span><span class="sxs-lookup"><span data-stu-id="15fb5-164">You can test this code using the following code in `Program.cs`:</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="15fb5-165">該程式碼包含在入門專案中，但已經標記為註解。移除註解，您就可以測試您撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15fb5-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="15fb5-166">您已經開始了解模式能如何協助您在程式碼和資料分離的情況下建立演算法。</span><span class="sxs-lookup"><span data-stu-id="15fb5-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="15fb5-167">`switch` 運算式會測試型別，並根據結果產生不同的值。</span><span class="sxs-lookup"><span data-stu-id="15fb5-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="15fb5-168">這只是個開頭。</span><span class="sxs-lookup"><span data-stu-id="15fb5-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="15fb5-169">新增承載率計費</span><span class="sxs-lookup"><span data-stu-id="15fb5-169">Add occupancy pricing</span></span>

<span data-ttu-id="15fb5-170">通行費主管機關想要鼓勵車輛在行駛時達到最大承載。</span><span class="sxs-lookup"><span data-stu-id="15fb5-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="15fb5-171">他們決定要對乘客較少的車輛收更多費用，並透過提供較低的費用來鼓勵車輛載滿乘客：</span><span class="sxs-lookup"><span data-stu-id="15fb5-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="15fb5-172">沒有乘客的汽車和計程車要付額外的 $0.50。</span><span class="sxs-lookup"><span data-stu-id="15fb5-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="15fb5-173">有兩個乘客的汽車和計程車可折價 0.50。</span><span class="sxs-lookup"><span data-stu-id="15fb5-173">Cars and taxis with two passengers get a 0.50 discount.</span></span>
- <span data-ttu-id="15fb5-174">有三個或更多乘客的汽車和計程車可折價 $1.00。</span><span class="sxs-lookup"><span data-stu-id="15fb5-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="15fb5-175">小於 50% 載滿的巴士要付額外的 $2.00。</span><span class="sxs-lookup"><span data-stu-id="15fb5-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="15fb5-176">大於 90% 載滿的巴士可折價 $1.00。</span><span class="sxs-lookup"><span data-stu-id="15fb5-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="15fb5-177">這些規則可以在相同的 switch 運算式中使用**屬性模式**來實作。</span><span class="sxs-lookup"><span data-stu-id="15fb5-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="15fb5-178">一旦判斷出型別，屬性模式就會檢查物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="15fb5-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="15fb5-179">單一的 `Car` 案例展開為四個不同案例：</span><span class="sxs-lookup"><span data-stu-id="15fb5-179">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="15fb5-180">前三個案例測試型別是否為 `Car`，然後檢查 `Passengers` 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="15fb5-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="15fb5-181">如果兩個都符合，系統就會評估該運算式並傳回。</span><span class="sxs-lookup"><span data-stu-id="15fb5-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="15fb5-182">您也可以用類似的方式來展開計程車的案例：</span><span class="sxs-lookup"><span data-stu-id="15fb5-182">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="15fb5-183">在上述範例中，最後一個案例省略了 `when` 子句。</span><span class="sxs-lookup"><span data-stu-id="15fb5-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="15fb5-184">接下來，藉由展開巴士的案例來實作承載率規則，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="15fb5-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

<span data-ttu-id="15fb5-185">通行費主管機關不在意貨車中的乘客數目。</span><span class="sxs-lookup"><span data-stu-id="15fb5-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="15fb5-186">相反地，他們是根據卡車的重量類別來收更多費用。</span><span class="sxs-lookup"><span data-stu-id="15fb5-186">Instead, they charge more based on the weight class of the trucks.</span></span> <span data-ttu-id="15fb5-187">超過 5000 磅的卡車要付額外的 $5.00。</span><span class="sxs-lookup"><span data-stu-id="15fb5-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span> <span data-ttu-id="15fb5-188">未滿 3000 磅的輕型卡車有美金 $2.00 元折扣。</span><span class="sxs-lookup"><span data-stu-id="15fb5-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span> <span data-ttu-id="15fb5-189">該規則使用下列程式碼來實作：</span><span class="sxs-lookup"><span data-stu-id="15fb5-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="15fb5-190">前一個程式碼顯示 switch 臂的 `when` 子句。</span><span class="sxs-lookup"><span data-stu-id="15fb5-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="15fb5-191">您使用 `when` 子句是測試條件，而不是屬性是否相等。</span><span class="sxs-lookup"><span data-stu-id="15fb5-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="15fb5-192">當您完成之後，就會有看起來像下面的方法：</span><span class="sxs-lookup"><span data-stu-id="15fb5-192">When you've finished, you'll have a method that looks much like the following:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="15fb5-193">這些 switch 臂許多都是**遞迴模式**的範例。</span><span class="sxs-lookup"><span data-stu-id="15fb5-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="15fb5-194">例如，`Car { Passengers: 1}` 顯示屬性模式內的常數模式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="15fb5-195">您可以使用巢狀 switch 讓此程式碼較不重複。</span><span class="sxs-lookup"><span data-stu-id="15fb5-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="15fb5-196">在上述範例中，`Car` 和 `Taxi` 都有四個不同的臂。</span><span class="sxs-lookup"><span data-stu-id="15fb5-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="15fb5-197">在這兩種情況下，您可以建立饋入屬性模式的型別模式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="15fb5-198">下列程式碼中顯示此技術：</span><span class="sxs-lookup"><span data-stu-id="15fb5-198">This technique is shown in the following code:</span></span>

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="15fb5-199">在上述範例中，使用遞迴運算式表示您不重複包含子臂 (測試屬性值) 的 `Car` 和 `Taxi` 臂。</span><span class="sxs-lookup"><span data-stu-id="15fb5-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="15fb5-200">此技術未用於 `Bus` 和 `DeliveryTruck` 臂，因為這些臂是測試屬性的範圍 (不是離散值)。</span><span class="sxs-lookup"><span data-stu-id="15fb5-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="15fb5-201">新增尖峰時段計費</span><span class="sxs-lookup"><span data-stu-id="15fb5-201">Add peak pricing</span></span>

<span data-ttu-id="15fb5-202">針對最後一個功能，通行費主管機關想要新增有時間性的尖峰時段計費。</span><span class="sxs-lookup"><span data-stu-id="15fb5-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="15fb5-203">在早上和晚上尖峰時段，通行費會加倍。</span><span class="sxs-lookup"><span data-stu-id="15fb5-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="15fb5-204">該規則只影響單向的交通：早上尖峰時段進入城市，以及晚上尖峰時段離開城市。</span><span class="sxs-lookup"><span data-stu-id="15fb5-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="15fb5-205">在工作日的其他時間，通行費增加 50%。</span><span class="sxs-lookup"><span data-stu-id="15fb5-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="15fb5-206">在半夜和清晨，通行費減少 25%。</span><span class="sxs-lookup"><span data-stu-id="15fb5-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="15fb5-207">在週末，無論時間皆為一般費率。</span><span class="sxs-lookup"><span data-stu-id="15fb5-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="15fb5-208">您會為此功能使用模式比對，但您會將它與其他技術整合。</span><span class="sxs-lookup"><span data-stu-id="15fb5-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="15fb5-209">您可以建置單一模式比對運算式，納入所有方向、星期幾和時間的組合。</span><span class="sxs-lookup"><span data-stu-id="15fb5-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="15fb5-210">結果會是一個複雜的運算式，</span><span class="sxs-lookup"><span data-stu-id="15fb5-210">The result would be a complicated expression.</span></span> <span data-ttu-id="15fb5-211">而它會難以閱讀及理解。</span><span class="sxs-lookup"><span data-stu-id="15fb5-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="15fb5-212">這樣會讓確認其正確性變得困難。</span><span class="sxs-lookup"><span data-stu-id="15fb5-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="15fb5-213">反之，結合那些方法來建立值的元組，一致地描述所有那些狀態。</span><span class="sxs-lookup"><span data-stu-id="15fb5-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="15fb5-214">然後使用模式比對來計算通行費的乘數。</span><span class="sxs-lookup"><span data-stu-id="15fb5-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="15fb5-215">元組包含三個不連續的條件：</span><span class="sxs-lookup"><span data-stu-id="15fb5-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="15fb5-216">星期是工作日或週末。</span><span class="sxs-lookup"><span data-stu-id="15fb5-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="15fb5-217">收取通行費時的時段。</span><span class="sxs-lookup"><span data-stu-id="15fb5-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="15fb5-218">方向是進入城市或離開城市</span><span class="sxs-lookup"><span data-stu-id="15fb5-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="15fb5-219">下表顯示輸入值和尖峰時段計費乘數的組合：</span><span class="sxs-lookup"><span data-stu-id="15fb5-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="15fb5-220">Day</span><span class="sxs-lookup"><span data-stu-id="15fb5-220">Day</span></span>        | <span data-ttu-id="15fb5-221">時間</span><span class="sxs-lookup"><span data-stu-id="15fb5-221">Time</span></span>         | <span data-ttu-id="15fb5-222">方向</span><span class="sxs-lookup"><span data-stu-id="15fb5-222">Direction</span></span> | <span data-ttu-id="15fb5-223">溢價</span><span class="sxs-lookup"><span data-stu-id="15fb5-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="15fb5-224">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-224">Weekday</span></span>    | <span data-ttu-id="15fb5-225">早上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-225">morning rush</span></span> | <span data-ttu-id="15fb5-226">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-226">inbound</span></span>   | <span data-ttu-id="15fb5-227">x 2.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-227">x 2.00</span></span>  |
| <span data-ttu-id="15fb5-228">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-228">Weekday</span></span>    | <span data-ttu-id="15fb5-229">早上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-229">morning rush</span></span> | <span data-ttu-id="15fb5-230">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-230">outbound</span></span>  | <span data-ttu-id="15fb5-231">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-231">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-232">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-232">Weekday</span></span>    | <span data-ttu-id="15fb5-233">日間</span><span class="sxs-lookup"><span data-stu-id="15fb5-233">daytime</span></span>      | <span data-ttu-id="15fb5-234">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-234">inbound</span></span>   | <span data-ttu-id="15fb5-235">x 1.50</span><span class="sxs-lookup"><span data-stu-id="15fb5-235">x 1.50</span></span>  |
| <span data-ttu-id="15fb5-236">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-236">Weekday</span></span>    | <span data-ttu-id="15fb5-237">日間</span><span class="sxs-lookup"><span data-stu-id="15fb5-237">daytime</span></span>      | <span data-ttu-id="15fb5-238">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-238">outbound</span></span>  | <span data-ttu-id="15fb5-239">x 1.50</span><span class="sxs-lookup"><span data-stu-id="15fb5-239">x 1.50</span></span>  |
| <span data-ttu-id="15fb5-240">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-240">Weekday</span></span>    | <span data-ttu-id="15fb5-241">晚上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-241">evening rush</span></span> | <span data-ttu-id="15fb5-242">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-242">inbound</span></span>   | <span data-ttu-id="15fb5-243">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-243">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-244">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-244">Weekday</span></span>    | <span data-ttu-id="15fb5-245">晚上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-245">evening rush</span></span> | <span data-ttu-id="15fb5-246">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-246">outbound</span></span>  | <span data-ttu-id="15fb5-247">x 2.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-247">x 2.00</span></span>  |
| <span data-ttu-id="15fb5-248">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-248">Weekday</span></span>    | <span data-ttu-id="15fb5-249">夜間</span><span class="sxs-lookup"><span data-stu-id="15fb5-249">overnight</span></span>    | <span data-ttu-id="15fb5-250">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-250">inbound</span></span>   | <span data-ttu-id="15fb5-251">x 0.75</span><span class="sxs-lookup"><span data-stu-id="15fb5-251">x 0.75</span></span>  |
| <span data-ttu-id="15fb5-252">工作日</span><span class="sxs-lookup"><span data-stu-id="15fb5-252">Weekday</span></span>    | <span data-ttu-id="15fb5-253">夜間</span><span class="sxs-lookup"><span data-stu-id="15fb5-253">overnight</span></span>    | <span data-ttu-id="15fb5-254">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-254">outbound</span></span>  | <span data-ttu-id="15fb5-255">x 0.75</span><span class="sxs-lookup"><span data-stu-id="15fb5-255">x 0.75</span></span>  |
| <span data-ttu-id="15fb5-256">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-256">Weekend</span></span>    | <span data-ttu-id="15fb5-257">早上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-257">morning rush</span></span> | <span data-ttu-id="15fb5-258">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-258">inbound</span></span>   | <span data-ttu-id="15fb5-259">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-259">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-260">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-260">Weekend</span></span>    | <span data-ttu-id="15fb5-261">早上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-261">morning rush</span></span> | <span data-ttu-id="15fb5-262">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-262">outbound</span></span>  | <span data-ttu-id="15fb5-263">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-263">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-264">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-264">Weekend</span></span>    | <span data-ttu-id="15fb5-265">日間</span><span class="sxs-lookup"><span data-stu-id="15fb5-265">daytime</span></span>      | <span data-ttu-id="15fb5-266">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-266">inbound</span></span>   | <span data-ttu-id="15fb5-267">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-267">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-268">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-268">Weekend</span></span>    | <span data-ttu-id="15fb5-269">日間</span><span class="sxs-lookup"><span data-stu-id="15fb5-269">daytime</span></span>      | <span data-ttu-id="15fb5-270">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-270">outbound</span></span>  | <span data-ttu-id="15fb5-271">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-271">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-272">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-272">Weekend</span></span>    | <span data-ttu-id="15fb5-273">晚上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-273">evening rush</span></span> | <span data-ttu-id="15fb5-274">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-274">inbound</span></span>   | <span data-ttu-id="15fb5-275">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-275">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-276">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-276">Weekend</span></span>    | <span data-ttu-id="15fb5-277">晚上尖峰時段</span><span class="sxs-lookup"><span data-stu-id="15fb5-277">evening rush</span></span> | <span data-ttu-id="15fb5-278">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-278">outbound</span></span>  | <span data-ttu-id="15fb5-279">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-279">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-280">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-280">Weekend</span></span>    | <span data-ttu-id="15fb5-281">夜間</span><span class="sxs-lookup"><span data-stu-id="15fb5-281">overnight</span></span>    | <span data-ttu-id="15fb5-282">進入</span><span class="sxs-lookup"><span data-stu-id="15fb5-282">inbound</span></span>   | <span data-ttu-id="15fb5-283">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-283">x 1.00</span></span>  |
| <span data-ttu-id="15fb5-284">週末</span><span class="sxs-lookup"><span data-stu-id="15fb5-284">Weekend</span></span>    | <span data-ttu-id="15fb5-285">夜間</span><span class="sxs-lookup"><span data-stu-id="15fb5-285">overnight</span></span>    | <span data-ttu-id="15fb5-286">離開</span><span class="sxs-lookup"><span data-stu-id="15fb5-286">outbound</span></span>  | <span data-ttu-id="15fb5-287">x 1.00</span><span class="sxs-lookup"><span data-stu-id="15fb5-287">x 1.00</span></span>  |

<span data-ttu-id="15fb5-288">三個變數的 16 個不同組合。</span><span class="sxs-lookup"><span data-stu-id="15fb5-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="15fb5-289">透過結合一些條件，您將會簡化最終的 switch 運算式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="15fb5-290">針對何時收取通行費，收取通行費的系統會使用 <xref:System.DateTime> 結構。</span><span class="sxs-lookup"><span data-stu-id="15fb5-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="15fb5-291">建置從上述表格建立變數的成員方法。</span><span class="sxs-lookup"><span data-stu-id="15fb5-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="15fb5-292">下列函式會使用模式比對 switch 運算式，表達 <xref:System.DateTime> 代表週末或工作日：</span><span class="sxs-lookup"><span data-stu-id="15fb5-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

<span data-ttu-id="15fb5-293">該方法可以運作，但它具重複性。</span><span class="sxs-lookup"><span data-stu-id="15fb5-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="15fb5-294">您可以簡化它，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="15fb5-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="15fb5-295">接下來，新增類似的函式來將時間分類為區塊：</span><span class="sxs-lookup"><span data-stu-id="15fb5-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="15fb5-296">先前的方法沒有使用模式比對。</span><span class="sxs-lookup"><span data-stu-id="15fb5-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="15fb5-297">使用類似的 `if` 陳述式串聯很清楚。</span><span class="sxs-lookup"><span data-stu-id="15fb5-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="15fb5-298">您要使用私用的 `enum` 將每個時間範圍轉換成離散值。</span><span class="sxs-lookup"><span data-stu-id="15fb5-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="15fb5-299">建立這些方法之後，您可以搭配使用另一個 `switch` 運算式和**元組模式**來計算計費溢價。</span><span class="sxs-lookup"><span data-stu-id="15fb5-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="15fb5-300">您可以建置有 16 個臂的 `switch` 運算式：</span><span class="sxs-lookup"><span data-stu-id="15fb5-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="15fb5-301">上面的程式碼可以運作，但它可以簡化。</span><span class="sxs-lookup"><span data-stu-id="15fb5-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="15fb5-302">週末的八個組合通行費都相同。</span><span class="sxs-lookup"><span data-stu-id="15fb5-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="15fb5-303">您可以用下列一行取代所有八個：</span><span class="sxs-lookup"><span data-stu-id="15fb5-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="15fb5-304">進入和離開的流量在工作日日間和夜間，都有相同的乘數。</span><span class="sxs-lookup"><span data-stu-id="15fb5-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="15fb5-305">這四個 switch 臂都可以替換成下列兩行：</span><span class="sxs-lookup"><span data-stu-id="15fb5-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="15fb5-306">經過這兩個變更之後，程式碼應該看起來像下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="15fb5-306">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

<span data-ttu-id="15fb5-307">最後，您可以移除收取一般價格的兩個尖峰時段。</span><span class="sxs-lookup"><span data-stu-id="15fb5-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="15fb5-308">移除那些臂之後，您可以將最後一個 switch 臂中的 `false` 取代為捨棄 (`_`)。</span><span class="sxs-lookup"><span data-stu-id="15fb5-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="15fb5-309">您會有下列已完成的方法：</span><span class="sxs-lookup"><span data-stu-id="15fb5-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="15fb5-310">此範例會醒目提示模式比對的優點之一：依序評估模式分支。</span><span class="sxs-lookup"><span data-stu-id="15fb5-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="15fb5-311">如果您重新排列它們，讓前面分支處理其中一個最近的案例，則編譯器會提出有關無法連線程式碼的警告。</span><span class="sxs-lookup"><span data-stu-id="15fb5-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="15fb5-312">那些語言規則讓您可以放心地進行上述簡化，而不需擔心程式碼會變更。</span><span class="sxs-lookup"><span data-stu-id="15fb5-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="15fb5-313">模式比對讓某些類型的程式碼更容易讀取，並在您無法將程式碼新增至類別時，提供物件導向技術的替代方式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="15fb5-314">雲端是造成資料和功能分開的原因。</span><span class="sxs-lookup"><span data-stu-id="15fb5-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="15fb5-315">資料的「圖形」與資料上的「作業」不需要一起描述。</span><span class="sxs-lookup"><span data-stu-id="15fb5-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="15fb5-316">在此教學課程中，您以和現有資料原始功能完全不同的方式取用它們。</span><span class="sxs-lookup"><span data-stu-id="15fb5-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="15fb5-317">模式比對讓您能夠撰寫覆寫這些類型的功能，即使您無法擴充它們。</span><span class="sxs-lookup"><span data-stu-id="15fb5-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="15fb5-318">後續步驟</span><span class="sxs-lookup"><span data-stu-id="15fb5-318">Next steps</span></span>

<span data-ttu-id="15fb5-319">您可以從 [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub 存放庫下載已完成的程式碼。</span><span class="sxs-lookup"><span data-stu-id="15fb5-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="15fb5-320">自行探索模式，並將此技術新增到您平常撰寫程式碼的活動中。</span><span class="sxs-lookup"><span data-stu-id="15fb5-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="15fb5-321">學習這些技巧提供您處理問題並建立新功能的另一種方式。</span><span class="sxs-lookup"><span data-stu-id="15fb5-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
