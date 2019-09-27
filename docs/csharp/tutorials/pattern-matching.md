---
title: 使用模式比對功能來擴充資料類型
description: 此進階教學課程示範如何使用模式比對技術，以個別建立的資料和演算法來建立功能。
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 036a6bcda04771eb8cf3699af8756e83bb144389
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332357"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>教學課程：使用模式比對功能來擴充資料類型

C# 7 引進基本的模式比對功能。 那些功能已在 C# 8 中擴充，有了新的運算式和模式。 您可以撰寫行為如同您擴充其他程式庫中之型別的功能。 模式的另一個用途是建立應用程式需要的功能，但該功能不是要擴充之型別的基本功能。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 辨識應該使用模式比對的情況。
> - 使用模式比對運算式根據類型和屬性值實作行為。
> - 結合模式比對與其他技術，建立完整的演算法。

## <a name="prerequisites"></a>必要條件

您必須設定電腦以執行 .NET Core，包括C# 8.0 編譯器。 從C# [Visual Studio 2019 16.3 版](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或[.net Core 3.0 SDK](https://dotnet.microsoft.com/download)開始，可以使用8個編譯器。

本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。

## <a name="scenarios-for-pattern-matching"></a>模式比對的案例

新式開發通常包括整合來自多個來源的資料，並在單一且一致的應用程式內呈現來自該資料的資訊和見解。 您和您的小組不會有代表傳入資料之所有型別的控制權和存取權。

傳統物件導向設計要求您在您的應用程式中建立型別，以代表來自多個資料來源的每個資料類型。 然後，您的應用程式會使用這些新型別、建立繼承階層、建立虛擬方法，以及實作抽象概念。 那些技術可以運作，而且有時候它們是最好的工具。 其他時候，您可以撰寫少一點程式碼。 透過使用將資料與操作該資料之作業分離的技術，您可以撰寫更清楚的程式碼。

在此教學課程中，您會建立並探索在單一情況下，接受來自數個外部來源之資料的應用程式。 您會了解**模式比對**如何提供有效率的方法，以不屬於原始系統的方式來取用及處理該資料。

請考慮使用通行費和尖峰時段計費來管理交通的主要都會區。 您要撰寫根據車輛類型計算其通行費的應用程式。 之後的改進會併入根據車輛中乘客數目的計費。 進一步的改進會新增根據時間和星期幾的計費。

從這個簡短描述，您可能已經快速地勾勒出建構此系統模型的階層。 不過，您的資料來自多個來源，如其他車輛註冊管理系統。 這些系統提供建構資料模型的不同類別，而且您沒有任何可用的單一物件模型。 在此教學課程中，您將使用這些簡化的類別，從來自外部系統的這些車輛資料建構模型，如下列程式碼所示：

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

您可以從 [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub 存放庫下載起始程式碼。 您可以看到車輛類別是來自不同的系統，且位於不同的命名空間中。 除了可用的 `System.Object` 之外，沒有通用的基底類別。

## <a name="pattern-matching-designs"></a>模式比對設計

本教學課程所使用案例會醒目提示適合以模式比對來解決的問題類型：

- 您要處理的物件不在符合您目標的物件階層中。 您可能會使用屬於不相關之系統的類別。
- 您要新增的功能不屬於這些類別的核心抽象概念。 車輛付的通行費隨不同類型的車輛而「變更」，但通行費不是車輛的核心函式。

當資料的「圖形」與資料上的「作業」不是一起描述時，C# 中的模式比對功能可讓它變得更容易使用。

## <a name="implement-the-basic-toll-calculations"></a>實作基本通行費計算

最基本的通行費計算僅依賴車輛類型：

- `Car` 是 $2.00。
- `Taxi` 是 $3.50。
- `Bus` 是 $5.00。
- `DeliveryTruck` 是 $10.00

建立新的 `TollCalculator` 類別，並在車輛類型上實作模式比對來取得通行費金額。 下列程式碼示範 `TollCalculator` 的初始實作。

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

上述程式碼使用可測試**型別模式**的 **switch 運算式** (與 [`switch`](../language-reference/keywords/switch.md) 陳述式不同)。 **switch 運算式**的開始是變數 (上述程式碼中的 `vehicle`)，接著是 `switch` 關鍵字。 然後所有的 **switch 臂**都在大括號內。 `switch` 運算式會對括住 `switch` 陳述式的語法進行其他細分。 已省略 `case` 關鍵字，且每個臂的結果都是運算式。 最後兩個臂顯示新的語言功能。 `{ }` 案例比對不符合先前臂的任何非 Null 物件。 此臂會攔截傳遞到此方法的任何不正確型別。  `{ }` 案例必須遵循每種車輛類型的案例。 順序如已顛倒，則 `{ }` 案例會優先。 最後，`null` 模式會偵測 `null` 於何時傳遞至這個方法。 因為其他型別模式只比對正確型別的非 Null 物件，所以 `null` 可以在最後。

您可以使用 `Program.cs` 中的下列程式碼來測試此程式碼：

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

該程式碼包含在入門專案中，但已經標記為註解。移除註解，您就可以測試您撰寫的程式碼。

您已經開始了解模式能如何協助您在程式碼和資料分離的情況下建立演算法。 `switch` 運算式會測試型別，並根據結果產生不同的值。 這只是個開頭。

## <a name="add-occupancy-pricing"></a>新增承載率計費

通行費主管機關想要鼓勵車輛在行駛時達到最大承載。 他們決定要對乘客較少的車輛收更多費用，並透過提供較低的費用來鼓勵車輛載滿乘客：

- 沒有乘客的汽車和計程車要付額外的 $0.50。
- 有兩名乘客的汽車和計程車可折價美金 $0.50 元。
- 有三個或更多乘客的汽車和計程車可折價 $1.00。
- 小於 50% 載滿的巴士要付額外的 $2.00。
- 大於 90% 載滿的巴士可折價 $1.00。

這些規則可以在相同的 switch 運算式中使用**屬性模式**來實作。 一旦判斷出型別，屬性模式就會檢查物件的屬性。 單一的 `Car` 案例展開為四個不同案例：

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

前三個案例測試型別是否為 `Car`，然後檢查 `Passengers` 屬性的值。 如果兩個都符合，系統就會評估該運算式並傳回。

您也可以用類似的方式來展開計程車的案例：

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

在上述範例中，最後一個案例省略了 `when` 子句。

接下來，藉由展開巴士的案例來實作承載率規則，如下列範例所示：

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

通行費主管機關不在意貨車中的乘客數目。 它們會根據卡車的重量類別調整通行費，如下所示：

- 超過 5000 磅的卡車要付額外的 $5.00。
- 未滿 3000 磅的輕型卡車有美金 $2.00 元折扣。

該規則使用下列程式碼來實作：

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

前一個程式碼顯示 switch 臂的 `when` 子句。 您使用 `when` 子句是測試條件，而不是屬性是否相等。 當您完成之後，就會有看起來像下面的方法：

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
    
    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

這些 switch 臂許多都是**遞迴模式**的範例。 例如，`Car { Passengers: 1}` 顯示屬性模式內的常數模式。

您可以使用巢狀 switch 讓此程式碼較不重複。 在上述範例中，`Car` 和 `Taxi` 都有四個不同的臂。 在這兩種情況下，您可以建立饋入屬性模式的型別模式。 下列程式碼中顯示此技術：

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

在上述範例中，使用遞迴運算式表示您不重複包含子臂 (測試屬性值) 的 `Car` 和 `Taxi` 臂。 此技術未用於 `Bus` 和 `DeliveryTruck` 臂，因為這些臂是測試屬性的範圍 (不是離散值)。

## <a name="add-peak-pricing"></a>新增尖峰時段計費

針對最後一個功能，通行費主管機關想要新增有時間性的尖峰時段計費。 在早上和晚上尖峰時段，通行費會加倍。 該規則只影響單向的交通：早上尖峰時段進入城市，以及晚上尖峰時段離開城市。 在工作日的其他時間，通行費增加 50%。 在半夜和清晨，通行費減少 25%。 在週末，無論時間皆為一般費率。

您會為此功能使用模式比對，但您會將它與其他技術整合。 您可以建置單一模式比對運算式，納入所有方向、星期幾和時間的組合。 結果會是一個複雜的運算式， 而它會難以閱讀及理解。 這樣會讓確認其正確性變得困難。 反之，結合那些方法來建立值的元組，一致地描述所有那些狀態。 然後使用模式比對來計算通行費的乘數。 元組包含三個不連續的條件：

- 星期是工作日或週末。
- 收取通行費時的時段。
- 方向是進入城市或離開城市

下表顯示輸入值和尖峰時段計費乘數的組合：

| Day        | Time         | Direction | 溢價 |
| ---------- | ------------ | --------- |--------:|
| 工作日    | 早上尖峰時段 | 進入   | x 2.00  |
| 工作日    | 早上尖峰時段 | 離開  | x 1.00  |
| 工作日    | 日間      | 進入   | x 1.50  |
| 工作日    | 日間      | 離開  | x 1.50  |
| 工作日    | 晚上尖峰時段 | 進入   | x 1.00  |
| 工作日    | 晚上尖峰時段 | 離開  | x 2.00  |
| 工作日    | 夜間    | 進入   | x 0.75  |
| 工作日    | 夜間    | 離開  | x 0.75  |
| 週末    | 早上尖峰時段 | 進入   | x 1.00  |
| 週末    | 早上尖峰時段 | 離開  | x 1.00  |
| 週末    | 日間      | 進入   | x 1.00  |
| 週末    | 日間      | 離開  | x 1.00  |
| 週末    | 晚上尖峰時段 | 進入   | x 1.00  |
| 週末    | 晚上尖峰時段 | 離開  | x 1.00  |
| 週末    | 夜間    | 進入   | x 1.00  |
| 週末    | 夜間    | 離開  | x 1.00  |

三個變數的 16 個不同組合。 透過結合一些條件，您將會簡化最終的 switch 運算式。

針對何時收取通行費，收取通行費的系統會使用 <xref:System.DateTime> 結構。 建置從上述表格建立變數的成員方法。 下列函式會使用模式比對 switch 運算式，表達 <xref:System.DateTime> 代表週末或工作日：

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

該方法可以運作，但它具重複性。 您可以簡化它，如下列程式碼所示：

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

接下來，新增類似的函式來將時間分類為區塊：

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

先前的方法沒有使用模式比對。 使用類似的 `if` 陳述式串聯很清楚。 您要使用私用的 `enum` 將每個時間範圍轉換成離散值。

建立這些方法之後，您可以搭配使用另一個 `switch` 運算式和**元組模式**來計算計費溢價。 您可以建置有 16 個臂的 `switch` 運算式：

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

上面的程式碼可以運作，但它可以簡化。 週末的八個組合通行費都相同。 您可以用下列一行取代所有八個：

```csharp
(false, _, _) => 1.0m,
```

進入和離開的流量在工作日日間和夜間，都有相同的乘數。 這四個 switch 臂都可以替換成下列兩行：

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

經過這兩個變更之後，程式碼應該看起來像下列程式碼：

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

最後，您可以移除收取一般價格的兩個尖峰時段。 移除那些臂之後，您可以將最後一個 switch 臂中的 `false` 取代為捨棄 (`_`)。 您會有下列已完成的方法：

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

此範例會醒目提示模式比對的優點之一：依序評估模式分支。 如果您重新排列它們，讓前面分支處理其中一個最近的案例，則編譯器會提出有關無法連線程式碼的警告。 那些語言規則讓您可以放心地進行上述簡化，而不需擔心程式碼會變更。

模式比對讓某些類型的程式碼更容易讀取，並在您無法將程式碼新增至類別時，提供物件導向技術的替代方式。 雲端是造成資料和功能分開的原因。 資料的「圖形」與資料上的「作業」不需要一起描述。 在此教學課程中，您以和現有資料原始功能完全不同的方式取用它們。 模式比對讓您能夠撰寫覆寫這些類型的功能，即使您無法擴充它們。

## <a name="next-steps"></a>後續步驟

您可以從 [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub 存放庫下載已完成的程式碼。 自行探索模式，並將此技術新增到您平常撰寫程式碼的活動中。 學習這些技巧提供您處理問題並建立新功能的另一種方式。
