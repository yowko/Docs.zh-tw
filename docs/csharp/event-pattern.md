---
title: 標準的 .NET 事件模式
description: 了解 .NET 事件模式、如何建立標準事件來源，以及如何訂閱和處理程式碼中的標準事件。
ms.date: 06/20/2016
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: 16a091dabe34a064ab3ee65a6d9f3e0ab36f1db4
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297032"
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="5925d-103">標準的 .NET 事件模式</span><span class="sxs-lookup"><span data-stu-id="5925d-103">Standard .NET event patterns</span></span>

[<span data-ttu-id="5925d-104">上一步</span><span class="sxs-lookup"><span data-stu-id="5925d-104">Previous</span></span>](events-overview.md)

<span data-ttu-id="5925d-105">.NET 事件通常會遵循少數已知的模式。</span><span class="sxs-lookup"><span data-stu-id="5925d-105">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="5925d-106">這些模式的標準化表示開發人員可以利用這些標準模式的知識，它們可套用至任何 .NET 事件程式。</span><span class="sxs-lookup"><span data-stu-id="5925d-106">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="5925d-107">讓我們先了解這些標準模式，以便您有建立標準事件來源所需的全部知識，在程式碼中訂閱並處理標準事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-107">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="5925d-108">事件委派簽章</span><span class="sxs-lookup"><span data-stu-id="5925d-108">Event Delegate Signatures</span></span>

<span data-ttu-id="5925d-109">.NET 事件委派的標準簽章是︰</span><span class="sxs-lookup"><span data-stu-id="5925d-109">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="5925d-110">傳回型別為 void。</span><span class="sxs-lookup"><span data-stu-id="5925d-110">The return type is void.</span></span> <span data-ttu-id="5925d-111">事件以委派為基礎，而且是多點傳送的委派。</span><span class="sxs-lookup"><span data-stu-id="5925d-111">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="5925d-112">支援任何事件來源的多個訂閱者。</span><span class="sxs-lookup"><span data-stu-id="5925d-112">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="5925d-113">來自方法的單一傳回值無法擴充至多個事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="5925d-113">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="5925d-114">引發事件後，事件來源看到哪一個傳回值？</span><span class="sxs-lookup"><span data-stu-id="5925d-114">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="5925d-115">您會在本文後面看到如何建立向事件來源報告資訊之支援事件訂閱者的事件通訊協定。</span><span class="sxs-lookup"><span data-stu-id="5925d-115">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="5925d-116">引數清單包含兩個引數︰寄件者及事件引數。</span><span class="sxs-lookup"><span data-stu-id="5925d-116">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="5925d-117">`sender` 的編譯時間類型是 `System.Object`，即使您可能知道一向正確之衍生程度較高的類型。</span><span class="sxs-lookup"><span data-stu-id="5925d-117">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="5925d-118">依照慣例使用 `object`。</span><span class="sxs-lookup"><span data-stu-id="5925d-118">By convention, use `object`.</span></span>

<span data-ttu-id="5925d-119">第二個引數一向是衍生自 `System.EventArgs` 的類型。</span><span class="sxs-lookup"><span data-stu-id="5925d-119">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="5925d-120">(您會在[下一篇](modern-events.md)看到此慣例已不再強制執行。)如果您的事件類型不需要任何其他引數，您仍要提供兩個引數。</span><span class="sxs-lookup"><span data-stu-id="5925d-120">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="5925d-121">您應該使用特殊值 `EventArgs.Empty` 來表示您的事件不包含任何額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="5925d-121">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="5925d-122">我們要組建一個類別，列出目錄中的檔案，或其遵循模式的任一子目錄。</span><span class="sxs-lookup"><span data-stu-id="5925d-122">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="5925d-123">每次找到符合模式的檔案，此元件都會引發事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-123">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="5925d-124">使用事件模型可提供一些設計優勢。</span><span class="sxs-lookup"><span data-stu-id="5925d-124">Using an event model provides some design advantages.</span></span> <span data-ttu-id="5925d-125">您可以建立多個事件接聽程式，於找到搜尋的檔案時，執行不同的動作。</span><span class="sxs-lookup"><span data-stu-id="5925d-125">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="5925d-126">結合不同的接聽程式可以建立更強固的演算法。</span><span class="sxs-lookup"><span data-stu-id="5925d-126">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="5925d-127">以下是尋找搜尋檔案的初始事件引數宣告︰</span><span class="sxs-lookup"><span data-stu-id="5925d-127">Here is the initial event argument declaration for finding a sought file:</span></span> 

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgsV1 "Define event arguments")]

<span data-ttu-id="5925d-128">即使這個類型看起來像是小型的僅限資料類型，您也應該遵循規範，讓它成為參考 (`class`) 類型。</span><span class="sxs-lookup"><span data-stu-id="5925d-128">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="5925d-129">這表示參考會傳遞引數物件，而所有訂閱者都會檢視資料的任何更新。</span><span class="sxs-lookup"><span data-stu-id="5925d-129">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="5925d-130">第一個版本是不可變的物件。</span><span class="sxs-lookup"><span data-stu-id="5925d-130">The first version is an immutable object.</span></span> <span data-ttu-id="5925d-131">您應該更偏好讓事件引數類型中的屬性成為不可變。</span><span class="sxs-lookup"><span data-stu-id="5925d-131">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="5925d-132">這樣一來，某個訂閱者就無法在其他訂閱者看到值之前變更值。</span><span class="sxs-lookup"><span data-stu-id="5925d-132">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="5925d-133">(以下是這個情況的例外狀況。)</span><span class="sxs-lookup"><span data-stu-id="5925d-133">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="5925d-134">接下來，我們需要在 FileSearcher 類別中建立事件宣告。</span><span class="sxs-lookup"><span data-stu-id="5925d-134">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="5925d-135">利用 `EventHandler<T>` 類型表示您還不需要建立另一個類型定義。</span><span class="sxs-lookup"><span data-stu-id="5925d-135">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="5925d-136">您只要使用一般的特製化即可。</span><span class="sxs-lookup"><span data-stu-id="5925d-136">You simply use a generic specialization.</span></span>

<span data-ttu-id="5925d-137">我們要填寫 FileSearcher 類別，以搜尋符合模式的檔案，並在發現相符項目時引發正確的事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-137">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

[!code-csharp[FileSearxcher](../../samples/csharp/events/Program.cs#FileSearcherV1 "Create the initial file searcher")]

## <a name="defining-and-raising-field-like-events"></a><span data-ttu-id="5925d-138">定義及引發的欄位型事件</span><span class="sxs-lookup"><span data-stu-id="5925d-138">Defining and Raising Field-Like Events</span></span>

<span data-ttu-id="5925d-139">將事件新增至類別的最簡單方式，是將該事件宣告為公用欄位，如上例所示︰</span><span class="sxs-lookup"><span data-stu-id="5925d-139">The simplest way to add an event to your class is to declare that event as a public field, as in the preceding example:</span></span>

[!code-csharp[DeclareEvent](../../samples/csharp/events/Program.cs#DeclareEvent "Declare the file found event")]

<span data-ttu-id="5925d-140">這看起來像是在宣告公用欄位，並會是不正確的物件導向做法。</span><span class="sxs-lookup"><span data-stu-id="5925d-140">This looks like it's declaring a public field, which would appear to be bad object-oriented practice.</span></span> <span data-ttu-id="5925d-141">您想要透過屬性或方法保護資料存取。</span><span class="sxs-lookup"><span data-stu-id="5925d-141">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="5925d-142">雖然這看起來不像正確的做法，但編譯器產生的程式碼確實會建立包裝函式，事件物件只能以安全的方式存取。</span><span class="sxs-lookup"><span data-stu-id="5925d-142">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="5925d-143">欄位型事件唯一可用的作業是新增處理常式︰</span><span class="sxs-lookup"><span data-stu-id="5925d-143">The only operations available on a field-like event are add handler:</span></span>

[!code-csharp[DeclareEventHandler](../../samples/csharp/events/Program.cs#DeclareEventHandler "Declare the file found event handler")]

<span data-ttu-id="5925d-144">以及移除處理常式：</span><span class="sxs-lookup"><span data-stu-id="5925d-144">and remove handler:</span></span>

[!code-csharp[RemoveEventHandler](../../samples/csharp/events/Program.cs#RemoveHandler "Remove the event handler")]

<span data-ttu-id="5925d-145">請注意，處理常式有區域變數。</span><span class="sxs-lookup"><span data-stu-id="5925d-145">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="5925d-146">如果使用了 Lambda 的主體，移除就無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="5925d-146">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="5925d-147">它會有不同的委派執行個體，不以無訊息模式執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="5925d-147">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="5925d-148">在類別之外的程式碼無法引發事件，也不能執行任何其他作業。</span><span class="sxs-lookup"><span data-stu-id="5925d-148">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="5925d-149">從事件訂閱者傳回值</span><span class="sxs-lookup"><span data-stu-id="5925d-149">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="5925d-150">您的簡單版本運作得很好。</span><span class="sxs-lookup"><span data-stu-id="5925d-150">Your simple version is working fine.</span></span> <span data-ttu-id="5925d-151">讓我們新增另一項功能︰取消。</span><span class="sxs-lookup"><span data-stu-id="5925d-151">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="5925d-152">當您引發找到的事件時，接聽程式應該能夠停止進一步的處理，如果此檔案是搜尋到的最後一個檔案。</span><span class="sxs-lookup"><span data-stu-id="5925d-152">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="5925d-153">事件處理常式不傳回值，因此您需要以另一種方式進行通訊。</span><span class="sxs-lookup"><span data-stu-id="5925d-153">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="5925d-154">標準事件模式使用 EventArgs 物件包含事件訂閱者可用於通訊取消的欄位。</span><span class="sxs-lookup"><span data-stu-id="5925d-154">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="5925d-155">根據「取消」合約的語意，有兩種不同的模式可以使用。</span><span class="sxs-lookup"><span data-stu-id="5925d-155">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="5925d-156">這兩種情況下，您都會將布林值欄位新增至找到之檔案事件的 EventArguments。</span><span class="sxs-lookup"><span data-stu-id="5925d-156">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="5925d-157">一種模式可讓任何一位訂閱者取消作業。</span><span class="sxs-lookup"><span data-stu-id="5925d-157">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="5925d-158">針對此模式，新的欄位會初始化為 `false`。</span><span class="sxs-lookup"><span data-stu-id="5925d-158">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="5925d-159">任何訂閱者都可以將它變更為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5925d-159">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="5925d-160">在所有訂閱者皆已看過引發的事件之後，FileSearcher 元件會檢查布林值並採取動作。</span><span class="sxs-lookup"><span data-stu-id="5925d-160">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="5925d-161">如果所有的訂閱者都想要取消作業，第二個模式只會取消作業。</span><span class="sxs-lookup"><span data-stu-id="5925d-161">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="5925d-162">在此模式中，新的欄位會初始化以指出應該取消的作業，而任何訂閱者皆可將它變更為表示作業應該繼續進行。</span><span class="sxs-lookup"><span data-stu-id="5925d-162">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="5925d-163">在所有訂閱者皆已看過引發的事件之後，FileSearcher 元件會檢查布林值並採取動作。</span><span class="sxs-lookup"><span data-stu-id="5925d-163">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="5925d-164">此模式有一個額外步驟︰元件需要知道是否有任何訂閱者已看到此事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-164">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="5925d-165">如果沒有任何訂閱者，則欄位會指出取消不正確。</span><span class="sxs-lookup"><span data-stu-id="5925d-165">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="5925d-166">我們要實作本例的第一個版本。</span><span class="sxs-lookup"><span data-stu-id="5925d-166">Let's implement the first version for this sample.</span></span> <span data-ttu-id="5925d-167">您需要將名為 `CancelRequested` 的布林值欄位加入到 `FileFoundArgs` 類型：</span><span class="sxs-lookup"><span data-stu-id="5925d-167">You need to add a boolean field named `CancelRequested` to the `FileFoundArgs` type:</span></span>

[!code-csharp[EventArgs](../../samples/csharp/events/Program.cs#EventArgs "Update event arguments")]

<span data-ttu-id="5925d-168">這個新欄位會自動初始化為 `false` (布林值欄位的預設值)，如此您就不會不小心取消。</span><span class="sxs-lookup"><span data-stu-id="5925d-168">This new Field is automatically initialized to `false`, the default value for a Boolean field, so you don't cancel accidentally.</span></span> <span data-ttu-id="5925d-169">元件僅有的其他變更是在引發事件後檢查旗標，查看是否有任何訂閱者曾要求取消︰</span><span class="sxs-lookup"><span data-stu-id="5925d-169">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

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

<span data-ttu-id="5925d-170">此模式的優點之一是，它不是一項重大變更。</span><span class="sxs-lookup"><span data-stu-id="5925d-170">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="5925d-171">以前沒有任何訂閱者要求取消，現在也沒有。</span><span class="sxs-lookup"><span data-stu-id="5925d-171">None of the subscribers requested a cancellation before, and they still are not.</span></span> <span data-ttu-id="5925d-172">沒有任何訂閱者程式碼需要更新，除非它們要支援新的取消通訊協定。</span><span class="sxs-lookup"><span data-stu-id="5925d-172">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="5925d-173">它是非常鬆散的耦合。</span><span class="sxs-lookup"><span data-stu-id="5925d-173">It's very loosely coupled.</span></span>

<span data-ttu-id="5925d-174">我們要更新訂閱者，以便它在找到第一個可執行檔之後，立刻要求取消︰</span><span class="sxs-lookup"><span data-stu-id="5925d-174">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="5925d-175">新增另一個事件宣告</span><span class="sxs-lookup"><span data-stu-id="5925d-175">Adding Another Event Declaration</span></span>

<span data-ttu-id="5925d-176">我們要再新增一項功能，示範事件的其他語言慣例。</span><span class="sxs-lookup"><span data-stu-id="5925d-176">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="5925d-177">新增 `Search` 方法的多載，此方法會周遊所有子目錄搜尋檔案。</span><span class="sxs-lookup"><span data-stu-id="5925d-177">Let's add an overload of the `Search` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="5925d-178">這在有許多子目錄的目錄中可能會是冗長的作業。</span><span class="sxs-lookup"><span data-stu-id="5925d-178">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="5925d-179">新增在每個新目錄搜尋開始時要引發的事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-179">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="5925d-180">這可讓訂閱者追蹤進度，將使用者更新為要處理的使用者。</span><span class="sxs-lookup"><span data-stu-id="5925d-180">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="5925d-181">您到目前為止建立的所有範例都是公用的。</span><span class="sxs-lookup"><span data-stu-id="5925d-181">All the samples you've created so far are public.</span></span> <span data-ttu-id="5925d-182">讓我們把這個變成內部事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-182">Let's make this one an internal event.</span></span> <span data-ttu-id="5925d-183">這表示您也可以將用於引數的類型變成內部。</span><span class="sxs-lookup"><span data-stu-id="5925d-183">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="5925d-184">您會從建立新的 EventArgs 衍生類別以報告新目錄和進度開始。</span><span class="sxs-lookup"><span data-stu-id="5925d-184">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

[!code-csharp[DirEventArgs](../../samples/csharp/events/Program.cs#SearchDirEventArgs "Define search directory event arguments")]

<span data-ttu-id="5925d-185">同樣地，您可以依照建議，為事件引數建立不可變的參考類型。</span><span class="sxs-lookup"><span data-stu-id="5925d-185">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="5925d-186">接下來定義事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-186">Next, define the event.</span></span> <span data-ttu-id="5925d-187">這次，您要使用不同的語法。</span><span class="sxs-lookup"><span data-stu-id="5925d-187">This time, you'll use a different syntax.</span></span> <span data-ttu-id="5925d-188">除了使用欄位語法，您也可以使用新增和移除處理常式來明確建立屬性。</span><span class="sxs-lookup"><span data-stu-id="5925d-188">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="5925d-189">在本範例中，那些處理常式中不需要額外的程式碼，但這會顯示您建立它們的方式。</span><span class="sxs-lookup"><span data-stu-id="5925d-189">In this sample, you won't need extra code in those handlers, but this shows how you would create them.</span></span>

[!code-csharp[Declare event with add and remove handlers](../../samples/csharp/events/Program.cs#DeclareSearchEvent "Declare the event with add and remove handlers")]

<span data-ttu-id="5925d-190">就很多方面而言，此處所撰寫的程式碼，可以對應到編譯器針對先前欄位事件定義所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5925d-190">In many ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="5925d-191">您建立事件所用的語法和用於[屬性](properties.md)的語法極其相似。</span><span class="sxs-lookup"><span data-stu-id="5925d-191">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="5925d-192">請注意，處理常式有不同的名稱︰`add` 和 `remove`。</span><span class="sxs-lookup"><span data-stu-id="5925d-192">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="5925d-193">分別表示訂閱事件，或取消訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-193">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="5925d-194">請注意，您也必須宣告私用支援欄位來儲存事件變數。</span><span class="sxs-lookup"><span data-stu-id="5925d-194">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="5925d-195">它會初始化為 Null。</span><span class="sxs-lookup"><span data-stu-id="5925d-195">It is initialized to null.</span></span>

<span data-ttu-id="5925d-196">接下來，我們要新增 `Search` 方法的多載，此方法會周遊子目錄並引發這兩個事件。</span><span class="sxs-lookup"><span data-stu-id="5925d-196">Next, let's add the overload of the `Search` method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="5925d-197">達成這個目的最簡單方式，是使用預設引數來指定您想要搜尋所有目錄︰</span><span class="sxs-lookup"><span data-stu-id="5925d-197">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

[!code-csharp[SearchImplementation](../../samples/csharp/events/Program.cs#FinalImplementation "Implementation to search directories")]

<span data-ttu-id="5925d-198">此時，您可以執行應用程式呼叫多載以搜尋所有子目錄。</span><span class="sxs-lookup"><span data-stu-id="5925d-198">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="5925d-199">新的 `ChangeDirectory` 事件沒有任何訂閱者，但使用 `?.Invoke()` 慣用語可確保其正確運作。</span><span class="sxs-lookup"><span data-stu-id="5925d-199">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="5925d-200">我們要新增處理常式寫入一行程式碼，在主控台視窗中顯示進度。</span><span class="sxs-lookup"><span data-stu-id="5925d-200">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

[!code-csharp[Search](../../samples/csharp/events/Program.cs#Search "Declare event handler")]

<span data-ttu-id="5925d-201">您已見過整個 .NET 生態系統所遵循的模式。</span><span class="sxs-lookup"><span data-stu-id="5925d-201">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="5925d-202">了解這些模式和慣例，您就能夠快速撰寫慣用的 C# 和 .NET。</span><span class="sxs-lookup"><span data-stu-id="5925d-202">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="5925d-203">接下來，您會在最新版本的 .NET 中看到這些模式的某些變更。</span><span class="sxs-lookup"><span data-stu-id="5925d-203">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="5925d-204">下一步</span><span class="sxs-lookup"><span data-stu-id="5925d-204">Next</span></span>](modern-events.md)
