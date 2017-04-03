---
title: "更新的 .NET Core 事件模式"
description: "更新的 .NET Core 事件模式"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d750209f2d970044aac2f3b8b119412a58595171
ms.lasthandoff: 03/13/2017

---

# <a name="the-updated-net-core-event-pattern"></a>更新的 .NET Core 事件模式

[上一步](event-pattern.md)

前一篇文章討論最常見的事件模式。 .NET Core 有比較寬鬆的模式。 在本版中，`EventHandler<TEventArgs>` 定義不再具有 `TEventArgs` 必須是 `System.EventArgs` 衍生類別的條件約束。

這為您增加彈性，且與舊版相容。 讓我們開始使用彈性。 System.EventArgs 類別導入了方法 `MemberwiseClone()`，它會建立物件的淺層複本。
該方法必須使用[反映](reflection.md)才能針對 `EventArgs` 的所有衍生類別實作其功能。 在特定的衍生類別中很容易建立該功能。 它會有效表示衍生自 System.EventArgs 的是條件約束，會限制您的設計，但不提供任何額外的好處。
事實上，您可以變更 `FileFoundArgs` 和 `SearchDirectoryArgs` 的定義，讓它們不衍生自 `EventArgs`。
程式運作完全相同。

您也可以將 `SearchDirectoryArgs` 變更 struct，如果還想再進行一項變更︰

```csharp  
internal struct SearchDirectoryArgs  
{  
    internal string CurrentSearchDirectory { get; }  
    internal int TotalDirs { get; }  
    internal int CompletedDirs { get; }  
    
    internal SearchDirectoryArgs(string dir, int totalDirs, 
        int completedDirs) : this()  
    {  
        CurrentSearchDirectory = dir;  
        TotalDirs = totalDirs;  
        CompletedDirs = completedDirs;  
    }  
}  
```   

其他的變更是先呼叫預設的建構函式，再輸入初始化所有欄位的建構函式。 若不新增，C# 的規則就會先報告正在存取屬性，再報告它們已被指派。

您不應該將 `FileFoundArgs` 從 class (參考型別) 變更為 struct (實值型別)。 這是因為處理取消的通訊協定需要以傳址方式傳遞事件引數。 如果進行了相同的變更，則檔案搜尋類別永遠不會觀察到任何事件訂閱者所做的任何變更。 新的結構複本會用於每個訂閱者，且該複本和檔案搜尋物件看到的複本不同。

接下來，我們要考慮如何讓這項變更與舊版相容。
移除條件約束不會影響任何現有的程式碼。 任何現有的事件引數型別仍衍生自 `System.EventArgs`。
回溯相容性是它們繼續衍生自 `System.EventArgs` 的一個主要原因。 任何現有的事件訂閱者都會是遵循傳統模式事件的訂閱者。

遵循類似的邏輯，現在建立的任何事件引數型別在任何現有程式碼基底中都沒有任何訂閱者。 非衍生自 `System.EventArgs` 的新事件型別不會中斷這些程式碼基底。

## <a name="events-with-async-subscribers"></a>有非同步訂閱者的事件

最後一個需要學習的模式︰如何正確撰寫呼叫非同步程式碼的事件訂閱者。 [async 和 await](async.md) 一文中會說明此挑戰。 非同步方法可以有 void 傳回型別，但強烈建議不要使用。 當您的事件訂閱者程式碼呼叫 async 方法時，您一定要建立 `async void` 方法。 事件處理常式簽章需要它。

您需要調解此相反的指導方針。 不過，您還是必須得建立安全的 `async void` 方法。 您需要實作的模式基本概念如下︰

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

首先，請注意處理常式會標示為非同步處理常式。 因為它被指派給事件處理常式委派型別，所以會有 void 傳回型別。 這表示您必須遵循處理常式中示範的模式，不允許從非同步處理常式的內容中擲回任何例外狀況。 因為它不會傳回工作，所以沒有任何工作會進入錯誤狀態來報告錯誤。 因為是非同步方法，所以方法不能只擲回例外狀況。 (呼叫方法會持續直執行，因為它是 `async`。)實際執行階段行為會針對不同的環境以不同的方式定義。 它可能會終止執行緒、可能會結束程式，或可能令程式處於未定狀態中。 以上這些都不是好結果。

這就是為什麼您應該將非同步工作的 await 陳述式包裝在自己的 try 區塊中。 如果它真的導致錯誤的工作，您可以記錄錯誤。 如果是您的應用程式無法復原的錯誤，您可以快速且正常地結束程式。

這些都是 .NET 事件模式的重大更新。 您會在使用的程式庫中看到許多舊版範例。 不過，您也應該了解最新的模式為何。

本系列的下一篇文章會幫助您分辨在設計中使用 `delegates` 和 `events`。 它們的概念類似，且該文章會協助您為程式做出最佳決定。

[下一步](distinguish-delegates-events.md)

