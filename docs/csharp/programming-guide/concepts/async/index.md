---
title: C# 中的非同步程式設計
description: 使用 async、await、Task 和 Task<T> 進行非同步程式設計的 C# 語言支援概觀
ms.date: 03/18/2019
ms.openlocfilehash: dc85fd4fb30278dc39c75c88d5fd23c1f1633366
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504362"
---
# <a name="the-task-asynchronous-programming-model-in-c"></a>C\# 中的非同步工作程式設計模型

非同步工作程式設計模型 (TAP) 在非同步程式碼上提供一個抽象層。 您可以和往常一樣，將程式碼撰寫成一連串的陳述式。 您可以將該程式碼讀成每個陳述式會先完成，再開始下一個陳述式。 編譯器會執行一些轉換，因為部分陳述式可能會開始工作，並傳回表示進行工作的 <xref:System.Threading.Tasks.Task>。

這是此語法的目標：讓程式碼讀起來就像是一連串的陳述式，但會根據外部資源配置和工作完成時間，以比較複雜的順序來執行。 這類似於人員為包含非同步工作之程序提供指示的方式。 在本文中，您將以準備早餐的指示為例，來了解 `async` 和 `await` 關鍵字如何讓您更輕鬆地理解包含一連串非同步指示的程式碼。 您撰寫了類似下列清單的指示，來說明如何準備早餐：

1. 倒杯咖啡。
1. 熱鍋，然後煎兩顆蛋。
1. 煎三片培根。
1. 烤兩片吐司。
1. 在吐司塗上奶油和果醬。
1. 倒杯柳橙汁。

如果您有烹飪經驗，您會**以非同步方式**來執行這些指示。 您會從為雞蛋熱鍋開始，然後開始煎培根。 等到將麵包放入烤麵包機，再開始煎蛋。 在程序的每個步驟，您會開始一個工作，然後將注意轉移到其他需要您注意的工作。

準備早餐很適合用來示範非平行的非同步工作。 一個人 (或執行緒) 可處理所有這些工作。 繼續以早餐為例，一個人可能會以非同步方式準備早餐，不等到第一個工作完成，就開始下一個工作。 不論是否有旁觀者，烹飪都會進行。 開始為雞蛋熱鍋之後，您可以開始煎培根。 等到開始煎培根，您可以將麵包放入烤麵包機。

若要進行平行演算法，您需要多個廚師 (或執行緒)。 一個人會負責煎蛋、一個人會負責煎培根，依此類推。 每個人只會專注於一個工作。 每個廚師 (或執行緒) 禁止以同步方式等候培根準備好翻面，或吐司彈出。 

現在，考慮將這些相同指示撰寫成 C# 陳述式：

[!code-csharp[SynchronousBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-starter/Program.cs#Main)]

電腦解譯這些指示的方式與人類不同。 電腦會封鎖每個陳述式，直到工作完成為止，再繼續下一個陳述式。 這會導致早餐無法令人滿意。 後續工作必須等到先前工作完成才會開始。 這會花更長的時間來準備早餐，且在上菜前，有些菜可能會變涼。 

如果您想要電腦以非同步方式執行上述指示，您必須撰寫非同步程式碼。

這些考量對您現今撰寫的程式很重要。 當您撰寫用戶端程式時，您想要 UI 可以回應使用者輸入。 您的應用程式不應該讓手機在從網路下載資料時呈現凍結。 當您撰寫伺服器程式時，您不想要執行緒被封鎖。 這些執行緒可能會服務其他要求。 在存在替代的非同步程式碼時使用同步程式碼，會導致您無法以較不耗費成本的方式擴充。 這些封鎖的執行緒會耗費成本。

現代化應用程式需要非同步程式碼才能成功。 由於沒有語言支援，撰寫非同步程式碼需要回呼、完成事件，或隱藏程式碼原本意圖的其他方式。 同步程式碼的優點是容易了解。 逐步動作讓您可以輕鬆地瀏覽與了解。 傳統非同步模型迫使您將重點放在程式碼的非同步本質，而不是程式碼的基本動作。

## <a name="dont-block-await-instead"></a>不要封鎖，而是等候

上述程式碼示範不正確的做法：建構同步程式碼來執行非同步作業。 如內容所指，此程式碼會防止執行緒執行任何其他工作。 在任何工作進行時，它不會遭到中斷。 就像是將麵包放入烤麵包機之後，直盯著烤麵包機。 在吐司彈出之前，您不會理會任何人對您說的話。 

我們將從更新此程式碼開始，讓執行緒在工作執行時不會遭到封鎖。 `await` 關鍵字提供一個非封鎖方式來開始工作，然後在工作完成時繼續執行。 準備早餐程式碼的一個簡單非同步版本看起來像下列程式碼片段：

[!code-csharp[SimpleAsyncBreakfast](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V2/Program.cs#Main)]

此程式碼不會在煎蛋或煎培根時封鎖其他工作。 但此程式碼也不會開始任何其他工作。 您仍會將吐司放入烤麵包機，並在彈出前直盯著它瞧。 但至少，您會回應任何需要您注意的人。 在點了多份早餐的餐廳中，廚師可能會在第一份早餐還在準備時，就開始準備另一份早餐。

現在，準備早餐的執行緒在等候任何已開始但尚未完成的工作時，不會遭到封鎖。 對於某些應用程式而言，只需要這項變更。 GUI 應用程式仍會只以這項變更來回應使用者。 不過在此案例中，您需要不只一項變更。 您不想要循序執行每個元件工作。 較好的做法是開始每個元件工作，然後等候先前的工作完成。

## <a name="start-tasks-concurrently"></a>同時開始工作

在許多情況下，您想要立即開始數個獨立工作。 然後，在每個工作完成時，您可以繼續其他準備好的工作。 以早餐為例，這會讓您更快速地完成早餐。 您也會幾乎同時完成所有工作。 因此，您會有熱騰騰的早餐。

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 和相關類型是您可以用來理解進行中工作的類別。 這可讓您撰寫出更類似您實際準備早餐方式的程式碼。 您會同時開始煎蛋、煎培根和烤吐司。 由於每個工作都需要執行動作，因此您會將注意轉移到該工作、處理下一個動作，然後等候其他需要您注意的工作。

您會開始一個工作，並保存表示該工作的 <xref:System.Threading.Tasks.Task> 物件。 您會 `await` 每個工作，再處理其結果。

我們將對早餐程式碼進行這些變更。 第一個步驟是為作業儲存開始時的工作，而不是等候工作：

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Egg eggs = await eggTask;
Console.WriteLine("eggs are ready");
Task<Bacon> baconTask = FryBacon(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Console.WriteLine("Breakfast is ready!");
```

接下來，您可以將培根與雞蛋的 `await` 陳述式移至方法結尾，並在供應早餐之前：

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");
Task<Egg> eggTask = FryEggs(2);
Task<Bacon> baconTask = FryBacon(3);
Task<Toast> toastTask = ToastBread(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

上述程式碼的效果更好。 您會同時開始所有非同步工作。 只有需要結果時，才會等候每個工作。 上述程式碼可能會類似於提出不同微服務要求，然後將結果合併成單一頁面的 Web 應用程式程式碼。 您會立即提出所有要求，然後 `await` 所有這些工作並撰寫網頁。

## <a name="composition-with-tasks"></a>工作組合

 您同時準備好早餐的每道菜，除吐司以外。 準備吐司是非同步作業 (烤土司) 以及同步作業 (塗上奶油和果醬) 的組合。 更新此程式碼說明一個重要概念：

> [!IMPORTANT]
> 非同步作業後面接著同步工作的組合會是非同步作業。 換句話說，如果作業有任何部分為非同步，則整個作業是非同步。

上述程式碼顯示您可以使用 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件來保存執行中的工作。 您會 `await` 每個工作，再使用其結果。 下一個步驟是建立表示其他工作組合的方法。 在供應早餐之前，您想要等候表示烤土司後再塗上奶油和果醬的工作。 您可以使用下列程式碼來表示該工作：

[!code-csharp[ComposeToastTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#ComposeToastTask)]

上述方法的簽章中有 `async` 修飾詞。 這會通知編譯器，此方法包含 `await` 陳述式，其中包含非同步作業。 此方法表示烤土司後再塗上奶油和果醬的工作。 此方法會傳回 <xref:System.Threading.Tasks.Task%601>，表示這三項作業的組合。 程式碼的 Main 區塊現在會變成：

[!code-csharp[StartConcurrentTasks](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-V3/Program.cs#Main)]

上述變更說明使用非同步程式碼的重要技術。 您可以透過分隔作業，將多個工作組合成傳回一個工作的新方法。 您可以選擇何時等候該工作。 您可以同時開始其他工作。

## <a name="await-tasks-efficiently"></a>有效率地等候工作

上述程式碼結尾的一連串 `await` 陳述式，可以透過 `Task` 類別的方法來改善。 其中一個 API 是 <xref:System.Threading.Tasks.Task.WhenAll%2A>，它會傳回其引數清單中所有工作都已完成時所完成的 <xref:System.Threading.Tasks.Task>，如下列程式碼所示：

```csharp
await Task.WhenAll(eggTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

另一個選項是使用 <xref:System.Threading.Tasks.Task.WhenAny%2A>，它會傳回其任何引數完成時所完成的 `Task<Task>`。 您可以等候傳回的工作，並知道它已完成。 下列程式碼範例示範如何使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 等候第一個工作完成，再處理其結果。 處理完成工作的結果之後，您會從傳遞至 `WhenAny` 的工作清單中移除該完成工作。

[!code-csharp[AwaitAnyTask](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#AwaitAnyTask)]

完成上述所有變更之後，`Main` 的最終版本看起來像下列程式碼：

[!code-csharp[Final](~/samples/snippets/csharp/tour-of-async/AsyncBreakfast-final/Program.cs#Main)]

此最終程式碼為非同步。 它會更精確地反映人員準備早餐的方式。 將上述程式碼與本文中的第一個程式碼範例做比較。 閱讀程式碼仍會清楚了解核心動作。 閱讀此程式碼的方式，如同閱讀本文開頭準備早餐的指示。 `async` 和 `await` 之語言功能為所有遵循下列書面指示的人員提供轉譯：盡可能開始多個工作且不要防止等候工作完成。
