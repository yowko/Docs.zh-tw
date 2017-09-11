---
title: "標準的 .NET 事件模式"
description: "標準的 .NET 事件模式"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 836866efc066f6d7dba64dd35ec694142c7eb70c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---

# <a name="the-standard-net-event-pattern"></a><span data-ttu-id="832fe-104">標準的 .NET 事件模式</span><span class="sxs-lookup"><span data-stu-id="832fe-104">The Standard .NET Event Pattern</span></span>

[<span data-ttu-id="832fe-105">上一篇</span><span class="sxs-lookup"><span data-stu-id="832fe-105">Previous</span></span>](events-overview.md)

<span data-ttu-id="832fe-106">.NET 事件通常會遵循少數已知的模式。</span><span class="sxs-lookup"><span data-stu-id="832fe-106">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="832fe-107">這些模式的標準化表示開發人員可以利用這些標準模式的知識，它們可套用至任何 .NET 事件程式。</span><span class="sxs-lookup"><span data-stu-id="832fe-107">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="832fe-108">讓我們先了解這些標準模式，以便您有建立標準事件來源所需的全部知識，在程式碼中訂閱並處理標準事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-108">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="832fe-109">事件委派簽章</span><span class="sxs-lookup"><span data-stu-id="832fe-109">Event Delegate Signatures</span></span>

<span data-ttu-id="832fe-110">.NET 事件委派的標準簽章是︰</span><span class="sxs-lookup"><span data-stu-id="832fe-110">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="832fe-111">傳回型別為 void。</span><span class="sxs-lookup"><span data-stu-id="832fe-111">The return type is void.</span></span> <span data-ttu-id="832fe-112">事件以委派為基礎，而且是多點傳送的委派。</span><span class="sxs-lookup"><span data-stu-id="832fe-112">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="832fe-113">支援任何事件來源的多個訂閱者。</span><span class="sxs-lookup"><span data-stu-id="832fe-113">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="832fe-114">來自方法的單一傳回值無法擴充至多個事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="832fe-114">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="832fe-115">引發事件後，事件來源看到哪一個傳回值？</span><span class="sxs-lookup"><span data-stu-id="832fe-115">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="832fe-116">您會在本文後面看到如何建立向事件來源報告資訊之支援事件訂閱者的事件通訊協定。</span><span class="sxs-lookup"><span data-stu-id="832fe-116">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="832fe-117">引數清單包含兩個引數︰寄件者及事件引數。</span><span class="sxs-lookup"><span data-stu-id="832fe-117">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="832fe-118">`sender` 的編譯時間類型是 `System.Object`，即使您可能知道一向正確之衍生程度較高的類型。</span><span class="sxs-lookup"><span data-stu-id="832fe-118">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="832fe-119">依照慣例使用 `object`。</span><span class="sxs-lookup"><span data-stu-id="832fe-119">By convention, use `object`.</span></span>

<span data-ttu-id="832fe-120">第二個引數一向是衍生自 `System.EventArgs` 的類型。</span><span class="sxs-lookup"><span data-stu-id="832fe-120">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="832fe-121">(您會在[下一篇](modern-events.md)看到此慣例已不再強制執行。)如果您的事件類型不需要任何其他引數，您仍要提供兩個引數。</span><span class="sxs-lookup"><span data-stu-id="832fe-121">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="832fe-122">您應該使用特殊值 `EventArgs.Empty` 來表示您的事件不包含任何額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="832fe-122">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="832fe-123">我們要組建一個類別，列出目錄中的檔案，或其遵循模式的任一子目錄。</span><span class="sxs-lookup"><span data-stu-id="832fe-123">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="832fe-124">每次找到符合模式的檔案，此元件都會引發事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-124">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="832fe-125">使用事件模型可提供一些設計優勢。</span><span class="sxs-lookup"><span data-stu-id="832fe-125">Using an event model provides some design advantages.</span></span> <span data-ttu-id="832fe-126">您可以建立多個事件接聽程式，於找到搜尋的檔案時，執行不同的動作。</span><span class="sxs-lookup"><span data-stu-id="832fe-126">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="832fe-127">結合不同的接聽程式可以建立更強固的演算法。</span><span class="sxs-lookup"><span data-stu-id="832fe-127">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="832fe-128">以下是尋找搜尋檔案的初始事件引數宣告︰</span><span class="sxs-lookup"><span data-stu-id="832fe-128">Here is the initial event argument declaration for finding a sought file:</span></span> 

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

<span data-ttu-id="832fe-129">即使這個類型看起來像是小型的僅限資料類型，您也應該遵循規範，讓它成為參考 (`class`) 類型。</span><span class="sxs-lookup"><span data-stu-id="832fe-129">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="832fe-130">這表示參考會傳遞引數物件，而所有訂閱者都會檢視資料的任何更新。</span><span class="sxs-lookup"><span data-stu-id="832fe-130">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="832fe-131">第一個版本是不可變的物件。</span><span class="sxs-lookup"><span data-stu-id="832fe-131">The first version is an immutable object.</span></span> <span data-ttu-id="832fe-132">您應該更偏好讓事件引數類型中的屬性成為不可變。</span><span class="sxs-lookup"><span data-stu-id="832fe-132">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="832fe-133">這樣一來，某個訂閱者就無法在其他訂閱者看到值之前變更值。</span><span class="sxs-lookup"><span data-stu-id="832fe-133">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="832fe-134">(以下是這個情況的例外狀況。)</span><span class="sxs-lookup"><span data-stu-id="832fe-134">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="832fe-135">接下來，我們需要在 FileSearcher 類別中建立事件宣告。</span><span class="sxs-lookup"><span data-stu-id="832fe-135">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="832fe-136">利用 `EventHandler<T>` 類型表示您還不需要建立另一個類型定義。</span><span class="sxs-lookup"><span data-stu-id="832fe-136">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="832fe-137">您只要使用一般的特製化即可。</span><span class="sxs-lookup"><span data-stu-id="832fe-137">You simply use a generic specialization.</span></span>

<span data-ttu-id="832fe-138">我們要填寫 FileSearcher 類別，以搜尋符合模式的檔案，並在發現相符項目時引發正確的事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-138">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

```csharp
public class FileSearcher
{
    public event EventHandler<FileFoundArgs> FileFound;

    public void Search(string directory, string searchPattern)
    {
        foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
        {
            FileFound?.Invoke(this, new FileFoundArgs(file));
        }
    }
}
```

## <a name="definining-and-raising-field-like-events"></a><span data-ttu-id="832fe-139">定義及引發的欄位型事件</span><span class="sxs-lookup"><span data-stu-id="832fe-139">Definining and Raising Field-Like Events</span></span>

<span data-ttu-id="832fe-140">將事件新增至類別的最簡單方式，是將該事件宣告為公用欄位，如上例所示︰</span><span class="sxs-lookup"><span data-stu-id="832fe-140">The simplest way to add an event to your class is to declare that event as a public field, as in the above example:</span></span>

```csharp
public event EventHandler<FileFoundArgs> FileFound;
```

<span data-ttu-id="832fe-141">這看起來像是宣告公用欄位，像是不正確的物件導向做法。</span><span class="sxs-lookup"><span data-stu-id="832fe-141">This looks like it's declaring a public field, which would appear to be bad object oriented practice.</span></span> <span data-ttu-id="832fe-142">您想要透過屬性或方法保護資料存取。</span><span class="sxs-lookup"><span data-stu-id="832fe-142">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="832fe-143">雖然這看起來不像正確的做法，但編譯器產生的程式碼確實會建立包裝函式，事件物件只能以安全的方式存取。</span><span class="sxs-lookup"><span data-stu-id="832fe-143">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="832fe-144">欄位型事件唯一可用的作業是新增處理常式︰</span><span class="sxs-lookup"><span data-stu-id="832fe-144">The only operations available on a field-like event are add handler:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);
lister.FileFound += onFIleFound;
```

<span data-ttu-id="832fe-145">以及移除處理常式：</span><span class="sxs-lookup"><span data-stu-id="832fe-145">and remove handler:</span></span>

```csharp
lister.FileFound -= onFileFound;
```

<span data-ttu-id="832fe-146">請注意，處理常式有區域變數。</span><span class="sxs-lookup"><span data-stu-id="832fe-146">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="832fe-147">如果使用了 Lambda 的主體，移除就無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="832fe-147">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="832fe-148">它會有不同的委派執行個體，不以無訊息模式執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="832fe-148">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="832fe-149">在類別之外的程式碼無法引發事件，也不能執行任何其他作業。</span><span class="sxs-lookup"><span data-stu-id="832fe-149">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="832fe-150">從事件訂閱者傳回值</span><span class="sxs-lookup"><span data-stu-id="832fe-150">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="832fe-151">您的簡單版本運作得很好。</span><span class="sxs-lookup"><span data-stu-id="832fe-151">Your simple version is working fine.</span></span> <span data-ttu-id="832fe-152">讓我們新增另一項功能︰取消。</span><span class="sxs-lookup"><span data-stu-id="832fe-152">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="832fe-153">當您引發找到的事件時，接聽程式應該能夠停止進一步的處理，如果此檔案是搜尋到的最後一個檔案。</span><span class="sxs-lookup"><span data-stu-id="832fe-153">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="832fe-154">事件處理常式不傳回值，因此您需要以另一種方式進行通訊。</span><span class="sxs-lookup"><span data-stu-id="832fe-154">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="832fe-155">標準事件模式使用 EventArgs 物件包含事件訂閱者可用於通訊取消的欄位。</span><span class="sxs-lookup"><span data-stu-id="832fe-155">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="832fe-156">根據「取消」合約的語意，有兩種不同的模式可以使用。</span><span class="sxs-lookup"><span data-stu-id="832fe-156">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="832fe-157">這兩種情況下，您都會將布林值欄位新增至找到之檔案事件的 EventArguments。</span><span class="sxs-lookup"><span data-stu-id="832fe-157">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="832fe-158">一種模式可讓任何一位訂閱者取消作業。</span><span class="sxs-lookup"><span data-stu-id="832fe-158">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="832fe-159">針對此模式，新的欄位會初始化為 `false`。</span><span class="sxs-lookup"><span data-stu-id="832fe-159">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="832fe-160">任何訂閱者都可以將它變更為 `true`。</span><span class="sxs-lookup"><span data-stu-id="832fe-160">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="832fe-161">在所有訂閱者皆已看過引發的事件之後，FileSearcher 元件會檢查布林值並採取動作。</span><span class="sxs-lookup"><span data-stu-id="832fe-161">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="832fe-162">如果所有的訂閱者都想要取消作業，第二個模式只會取消作業。</span><span class="sxs-lookup"><span data-stu-id="832fe-162">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="832fe-163">在此模式中，新的欄位會初始化以指出應該取消的作業，而任何訂閱者皆可將它變更為表示作業應該繼續進行。</span><span class="sxs-lookup"><span data-stu-id="832fe-163">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="832fe-164">在所有訂閱者皆已看過引發的事件之後，FileSearcher 元件會檢查布林值並採取動作。</span><span class="sxs-lookup"><span data-stu-id="832fe-164">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="832fe-165">此模式有一個額外步驟︰元件需要知道是否有任何訂閱者已看到此事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-165">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="832fe-166">如果沒有任何訂閱者，則欄位會指出取消不正確。</span><span class="sxs-lookup"><span data-stu-id="832fe-166">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="832fe-167">我們要實作本例的第一個版本。</span><span class="sxs-lookup"><span data-stu-id="832fe-167">Let's implement the first version for this sample.</span></span> <span data-ttu-id="832fe-168">您需要將布林值欄位新增至 FileFoundEventArgs 類型︰</span><span class="sxs-lookup"><span data-stu-id="832fe-168">You need to add a boolean field to the FileFoundEventArgs type:</span></span>

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }
    public bool CancelRequested { get; set; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

<span data-ttu-id="832fe-169">這個新欄位應該初始化為 false，因此取消要有理由。</span><span class="sxs-lookup"><span data-stu-id="832fe-169">This new Field should be initialized to false, so you don't cancel for no reason.</span></span> <span data-ttu-id="832fe-170">這是布林值欄位的預設值，因此會自動進行。</span><span class="sxs-lookup"><span data-stu-id="832fe-170">That is the default value for a boolean field, so that happens automatically.</span></span> <span data-ttu-id="832fe-171">元件僅有的其他變更是在引發事件後檢查旗標，查看是否有任何訂閱者曾要求取消︰</span><span class="sxs-lookup"><span data-stu-id="832fe-171">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="832fe-172">此模式的優點之一是，它不是一項重大變更。</span><span class="sxs-lookup"><span data-stu-id="832fe-172">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="832fe-173">以前沒有任何訂閱者要求取消，現在也沒有。</span><span class="sxs-lookup"><span data-stu-id="832fe-173">None of the subscribers requested a cancel before, and they still are not.</span></span> <span data-ttu-id="832fe-174">沒有任何訂閱者程式碼需要更新，除非它們要支援新的取消通訊協定。</span><span class="sxs-lookup"><span data-stu-id="832fe-174">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="832fe-175">它是非常鬆散的耦合。</span><span class="sxs-lookup"><span data-stu-id="832fe-175">It's very loosely coupled.</span></span>

<span data-ttu-id="832fe-176">我們要更新訂閱者，以便它在找到第一個可執行檔之後，立刻要求取消︰</span><span class="sxs-lookup"><span data-stu-id="832fe-176">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="832fe-177">新增另一個事件宣告</span><span class="sxs-lookup"><span data-stu-id="832fe-177">Adding Another Event Declaration</span></span>

<span data-ttu-id="832fe-178">我們要再新增一項功能，示範事件的其他語言慣例。</span><span class="sxs-lookup"><span data-stu-id="832fe-178">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="832fe-179">新增 `Search()` 方法的多載，此方法會周遊所有子目錄搜尋檔案。</span><span class="sxs-lookup"><span data-stu-id="832fe-179">Let's add an overload of the `Search()` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="832fe-180">這在有許多子目錄的目錄中可能會是冗長的作業。</span><span class="sxs-lookup"><span data-stu-id="832fe-180">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="832fe-181">新增在每個新目錄搜尋開始時要引發的事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-181">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="832fe-182">這可讓訂閱者追蹤進度，將使用者更新為要處理的使用者。</span><span class="sxs-lookup"><span data-stu-id="832fe-182">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="832fe-183">您到目前為止建立的所有範例都是公用的。</span><span class="sxs-lookup"><span data-stu-id="832fe-183">All the samples you've created so far are public.</span></span> <span data-ttu-id="832fe-184">讓我們把這個變成內部事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-184">Let's make this one an internal event.</span></span> <span data-ttu-id="832fe-185">這表示您也可以將用於引數的類型變成內部。</span><span class="sxs-lookup"><span data-stu-id="832fe-185">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="832fe-186">您會從建立新的 EventArgs 衍生類別以報告新目錄和進度開始。</span><span class="sxs-lookup"><span data-stu-id="832fe-186">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

```csharp
internal class SearchDirectoryArgs : EventArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs)
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
``` 

<span data-ttu-id="832fe-187">同樣地，您可以依照建議，為事件引數建立不可變的參考類型。</span><span class="sxs-lookup"><span data-stu-id="832fe-187">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="832fe-188">接下來定義事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-188">Next, define the event.</span></span> <span data-ttu-id="832fe-189">這次，您要使用不同的語法。</span><span class="sxs-lookup"><span data-stu-id="832fe-189">This time, you'll use a different syntax.</span></span> <span data-ttu-id="832fe-190">除了使用欄位語法，您也可以使用新增和移除處理常式來明確建立屬性。</span><span class="sxs-lookup"><span data-stu-id="832fe-190">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="832fe-191">在本例中，此專案的這些處理常式中不需要額外的程式碼，但這會顯示您建立它們的方式。</span><span class="sxs-lookup"><span data-stu-id="832fe-191">In this sample, you won't need extra code in those handlers in this project, but this shows how you would create them.</span></span>

```csharp
internal event EventHandler<SearchDirectoryArgs> DirectoryChanged
{
    add { directoryChanged += value; }
    remove { directoryChanged -= value; }
}
private EventHandler<SearchDirectoryArgs> directoryChanged;
```

<span data-ttu-id="832fe-192">您在此撰寫的程式碼，有很多方式會鏡像編譯器為欄位事件定義產生的程式碼，這些程式碼您稍早已見過。</span><span class="sxs-lookup"><span data-stu-id="832fe-192">In may ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="832fe-193">您建立事件所用的語法和用於[屬性](properties.md)的語法極其相似。</span><span class="sxs-lookup"><span data-stu-id="832fe-193">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="832fe-194">請注意，處理常式有不同的名稱︰`add` 和 `remove`。</span><span class="sxs-lookup"><span data-stu-id="832fe-194">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="832fe-195">分別表示訂閱事件，或取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-195">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="832fe-196">請注意，您也必須宣告私用支援欄位來儲存事件變數。</span><span class="sxs-lookup"><span data-stu-id="832fe-196">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="832fe-197">它會初始化為 Null。</span><span class="sxs-lookup"><span data-stu-id="832fe-197">It is initialized to null.</span></span>

<span data-ttu-id="832fe-198">接下來，我們要新增 Search() 方法的多載，此方法會周遊子目錄並引發這兩個事件。</span><span class="sxs-lookup"><span data-stu-id="832fe-198">Next, let's add the overload of the Search() method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="832fe-199">達成這個目的最簡單方式，是使用預設引數來指定您想要搜尋所有目錄︰</span><span class="sxs-lookup"><span data-stu-id="832fe-199">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

```csharp
public void Search(string directory, string searchPattern, bool searchSubDirs = false)
{
    if (searchSubDirs)
    {
        var allDirectories = Directory.GetDirectories(directory, "*.*", SearchOption.AllDirectories);
        var completedDirs = 0;
        var totalDirs = allDirectories.Length + 1;
        foreach (var dir in allDirectories)
        {
            directoryChanged?.Invoke(this,
                new SearchDirectoryArgs(dir, totalDirs, completedDirs++));
            // Recursively search this child directory:
            SearchDirectory(dir, searchPattern);
        }
        // Include the Current Directory:
        directoryChanged?.Invoke(this,
            new SearchDirectoryArgs(directory, totalDirs, completedDirs++));
        SearchDirectory(directory, searchPattern);
    }
    else
    {
        SearchDirectory(directory, searchPattern);
    }
}

private void SearchDirectory(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="832fe-200">此時，您可以執行應用程式呼叫多載以搜尋所有子目錄。</span><span class="sxs-lookup"><span data-stu-id="832fe-200">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="832fe-201">新的 `ChangeDirectory` 事件沒有任何訂閱者，但使用 `?.Invoke()` 慣用語可確保其正確運作。</span><span class="sxs-lookup"><span data-stu-id="832fe-201">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="832fe-202">我們要新增處理常式寫入一行程式碼，在主控台視窗中顯示進度。</span><span class="sxs-lookup"><span data-stu-id="832fe-202">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

```csharp
lister.DirectoryChanged += (sender, eventArgs) =>
{
    Console.Write($"Entering '{eventArgs.CurrentSearchDirectory}'.");
    Console.WriteLine($" {eventArgs.CompletedDirs} of {eventArgs.TotalDirs} completed...");
};
```

<span data-ttu-id="832fe-203">您已見過整個 .NET 生態系統所遵循的模式。</span><span class="sxs-lookup"><span data-stu-id="832fe-203">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="832fe-204">了解這些模式和慣例，您就能夠快速撰寫慣用的 C# 和 .NET。</span><span class="sxs-lookup"><span data-stu-id="832fe-204">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="832fe-205">接下來，您會在最新版本的 .NET 中看到這些模式的某些變更。</span><span class="sxs-lookup"><span data-stu-id="832fe-205">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="832fe-206">下一篇</span><span class="sxs-lookup"><span data-stu-id="832fe-206">Next</span></span>](modern-events.md)

