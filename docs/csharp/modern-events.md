---
title: 更新的 .NET Core 事件模式
description: 了解 .NET Core 事件模式如何啟用回溯相容性的彈性，以及如何使用非同步訂閱者來實作安全事件處理。
ms.date: 06/20/2016
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: 158295215932f54c75afdf1e96d48453434129fe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751780"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="96017-103">更新的 .NET Core 事件模式</span><span class="sxs-lookup"><span data-stu-id="96017-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="96017-104">上一步</span><span class="sxs-lookup"><span data-stu-id="96017-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="96017-105">前一篇文章討論最常見的事件模式。</span><span class="sxs-lookup"><span data-stu-id="96017-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="96017-106">.NET Core 有比較寬鬆的模式。</span><span class="sxs-lookup"><span data-stu-id="96017-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="96017-107">在本版中，`EventHandler<TEventArgs>` 定義不再具有 `TEventArgs` 必須是 `System.EventArgs` 衍生類別的條件約束。</span><span class="sxs-lookup"><span data-stu-id="96017-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="96017-108">這為您增加彈性，且與舊版相容。</span><span class="sxs-lookup"><span data-stu-id="96017-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="96017-109">讓我們開始使用彈性。</span><span class="sxs-lookup"><span data-stu-id="96017-109">Let's start with the flexibility.</span></span> <span data-ttu-id="96017-110">System.EventArgs 類別導入了方法 `MemberwiseClone()`，它會建立物件的淺層複本。</span><span class="sxs-lookup"><span data-stu-id="96017-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="96017-111">該方法必須使用反映，才能針對 `EventArgs` 的任何衍生類別實作其功能。</span><span class="sxs-lookup"><span data-stu-id="96017-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="96017-112">在特定的衍生類別中很容易建立該功能。</span><span class="sxs-lookup"><span data-stu-id="96017-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="96017-113">它會有效表示衍生自 System.EventArgs 的是條件約束，會限制您的設計，但不提供任何額外的好處。</span><span class="sxs-lookup"><span data-stu-id="96017-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="96017-114">事實上，您可以變更 `FileFoundArgs` 與 `SearchDirectoryArgs` 的定義，讓它們不衍生自 `EventArgs`。</span><span class="sxs-lookup"><span data-stu-id="96017-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="96017-115">程式運作完全相同。</span><span class="sxs-lookup"><span data-stu-id="96017-115">The program will work exactly the same.</span></span>

<span data-ttu-id="96017-116">如果您再進行一項變更，還可以將 `SearchDirectoryArgs` 變更為結構：</span><span class="sxs-lookup"><span data-stu-id="96017-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="96017-117">其他的變更，是在輸入初始化所有欄位的建構函式前呼叫無參數建構函式。</span><span class="sxs-lookup"><span data-stu-id="96017-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="96017-118">若不新增，C# 的規則就會先報告正在存取屬性，再報告它們已被指派。</span><span class="sxs-lookup"><span data-stu-id="96017-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="96017-119">您不應該將 `FileFoundArgs` 從 class (參考型別) 變更為 struct (實值型別)。</span><span class="sxs-lookup"><span data-stu-id="96017-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="96017-120">這是因為處理取消的通訊協定需要以傳址方式傳遞事件引數。</span><span class="sxs-lookup"><span data-stu-id="96017-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="96017-121">如果進行了相同的變更，則檔案搜尋類別永遠不會觀察到任何事件訂閱者所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="96017-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="96017-122">新的結構複本會用於每個訂閱者，且該複本和檔案搜尋物件看到的複本不同。</span><span class="sxs-lookup"><span data-stu-id="96017-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="96017-123">接下來，我們要考慮如何讓這項變更與舊版相容。</span><span class="sxs-lookup"><span data-stu-id="96017-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="96017-124">移除條件約束不會影響任何現有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="96017-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="96017-125">任何現有的事件引數型別仍衍生自 `System.EventArgs`。</span><span class="sxs-lookup"><span data-stu-id="96017-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="96017-126">回溯相容性是它們繼續衍生自 `System.EventArgs` 的一個主要原因。</span><span class="sxs-lookup"><span data-stu-id="96017-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="96017-127">任何現有的事件訂閱者都會是遵循傳統模式事件的訂閱者。</span><span class="sxs-lookup"><span data-stu-id="96017-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="96017-128">遵循類似的邏輯，現在建立的任何事件引數型別在任何現有程式碼基底中都沒有任何訂閱者。</span><span class="sxs-lookup"><span data-stu-id="96017-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="96017-129">非衍生自 `System.EventArgs` 的新事件型別不會中斷這些程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="96017-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="96017-130">有非同步訂閱者的事件</span><span class="sxs-lookup"><span data-stu-id="96017-130">Events with Async subscribers</span></span>

<span data-ttu-id="96017-131">您還有最後一個要了解的模式：如何正確撰寫呼叫非同步程式碼的事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="96017-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="96017-132">[async 和 await](async.md) 一文中會說明此挑戰。</span><span class="sxs-lookup"><span data-stu-id="96017-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="96017-133">非同步方法可以有 void 傳回型別，但強烈建議不要使用。</span><span class="sxs-lookup"><span data-stu-id="96017-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="96017-134">當您的事件訂閱者程式碼呼叫 async 方法時，您一定要建立 `async void` 方法。</span><span class="sxs-lookup"><span data-stu-id="96017-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="96017-135">事件處理常式簽章需要它。</span><span class="sxs-lookup"><span data-stu-id="96017-135">The event handler signature requires it.</span></span>

<span data-ttu-id="96017-136">您需要調解此相反的指導方針。</span><span class="sxs-lookup"><span data-stu-id="96017-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="96017-137">不過，您還是必須得建立安全的 `async void` 方法。</span><span class="sxs-lookup"><span data-stu-id="96017-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="96017-138">您需要實作的模式基本概念如下︰</span><span class="sxs-lookup"><span data-stu-id="96017-138">The basics of the pattern you need to implement are below:</span></span>

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

<span data-ttu-id="96017-139">首先，請注意處理常式會標示為非同步處理常式。</span><span class="sxs-lookup"><span data-stu-id="96017-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="96017-140">因為它被指派給事件處理常式委派型別，所以會有 void 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="96017-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="96017-141">這表示您必須遵循處理常式中示範的模式，不允許從非同步處理常式的內容中擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="96017-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="96017-142">因為它不會傳回工作，所以沒有任何工作會進入錯誤狀態來報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="96017-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="96017-143">因為是非同步方法，所以方法不能只擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="96017-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="96017-144">(呼叫方法會持續直執行，因為它是 `async`。)實際執行階段行為會針對不同的環境以不同的方式定義。</span><span class="sxs-lookup"><span data-stu-id="96017-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="96017-145">它可能會終止執行緒、可能會結束程式，或可能令程式處於未定狀態中。</span><span class="sxs-lookup"><span data-stu-id="96017-145">It may terminate the thread, it may terminate the program, or it may leave the program in an undetermined state.</span></span> <span data-ttu-id="96017-146">以上這些都不是好結果。</span><span class="sxs-lookup"><span data-stu-id="96017-146">None of those are good outcomes.</span></span>

<span data-ttu-id="96017-147">這就是為什麼您應該將非同步工作的 await 陳述式包裝在自己的 try 區塊中。</span><span class="sxs-lookup"><span data-stu-id="96017-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="96017-148">如果它真的導致錯誤的工作，您可以記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="96017-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="96017-149">如果是您的應用程式無法復原的錯誤，您可以快速且正常地結束程式。</span><span class="sxs-lookup"><span data-stu-id="96017-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="96017-150">這些都是 .NET 事件模式的重大更新。</span><span class="sxs-lookup"><span data-stu-id="96017-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="96017-151">您會在使用的程式庫中看到許多舊版範例。</span><span class="sxs-lookup"><span data-stu-id="96017-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="96017-152">不過，您也應該了解最新的模式為何。</span><span class="sxs-lookup"><span data-stu-id="96017-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="96017-153">本系列的下一篇文章會幫助您分辨在設計中使用 `delegates` 和 `events`。</span><span class="sxs-lookup"><span data-stu-id="96017-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="96017-154">它們的概念類似，且該文章會協助您為程式做出最佳決定。</span><span class="sxs-lookup"><span data-stu-id="96017-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="96017-155">下一步</span><span class="sxs-lookup"><span data-stu-id="96017-155">Next</span></span>](distinguish-delegates-events.md)
