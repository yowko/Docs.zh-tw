---
title: "使用 Async 和 Await 進行非同步程式設計 (C#)"
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6822143df2d02c284d7506d180139c18cfbaf370
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="asynchronous-programming-with-async-and-await-c"></a><span data-ttu-id="b8382-102">使用 async 和 await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-102">Asynchronous programming with async and await (C#)</span></span>
<span data-ttu-id="b8382-103">您可以使用非同步程式設計，避免發生效能瓶頸並增強應用程式的整體回應性。</span><span class="sxs-lookup"><span data-stu-id="b8382-103">You can avoid performance bottlenecks and enhance the overall responsiveness of your application by using asynchronous programming.</span></span> <span data-ttu-id="b8382-104">不過，撰寫非同步應用程式的傳統技術可能很複雜，因而難以撰寫、偵錯和維護。</span><span class="sxs-lookup"><span data-stu-id="b8382-104">However, traditional techniques for writing asynchronous applications can be complicated, making them difficult to write, debug, and maintain.</span></span>  
  
<span data-ttu-id="b8382-105">[C# 5](../../../whats-new/index.md#previous-versions) 引進了一種簡化的方法 (非同步程式設計)，來運用 .NET Framework 4.5 和更新版本、.NET Core 以及 Windows 執行階段中的非同步支援。</span><span class="sxs-lookup"><span data-stu-id="b8382-105">[C# 5](../../../whats-new/index.md#previous-versions) introduced a simplified approach, async programming, that leverages asynchronous support in the .NET Framework 4.5 and higher, .NET Core, and the Windows Runtime.</span></span> <span data-ttu-id="b8382-106">編譯器會代替開發人員處理過去經常要處理的困難工作，而您的應用程式仍保有類似同步程式碼的邏輯結構。</span><span class="sxs-lookup"><span data-stu-id="b8382-106">The compiler does the difficult work that the developer used to do, and your application retains a logical structure that resembles synchronous code.</span></span> <span data-ttu-id="b8382-107">因此，您可以輕鬆擁有非同步程式設計的所有優點。</span><span class="sxs-lookup"><span data-stu-id="b8382-107">As a result, you get all the advantages of asynchronous programming with a fraction of the effort.</span></span>  
  
<span data-ttu-id="b8382-108">本主題提供使用非同步程式設計的時機和使用方式的概觀，並加入包含詳細資料及範例的支援主題連結。</span><span class="sxs-lookup"><span data-stu-id="b8382-108">This topic provides an overview of when and how to use async programming and includes links to support topics that contain details and examples.</span></span>  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> <span data-ttu-id="b8382-109">非同步可改善回應性</span><span class="sxs-lookup"><span data-stu-id="b8382-109">Async improves responsiveness</span></span>  
 <span data-ttu-id="b8382-110">非同步對於可能在像是 Web 存取時會進行封鎖的活動而言相當重要。</span><span class="sxs-lookup"><span data-stu-id="b8382-110">Asynchrony is essential for activities that are potentially blocking, such as web access.</span></span> <span data-ttu-id="b8382-111">存取 Web 資源的速度有時會變慢或延遲。</span><span class="sxs-lookup"><span data-stu-id="b8382-111">Access to a web resource sometimes is slow or delayed.</span></span> <span data-ttu-id="b8382-112">如果這類活動在同步處理序中遭到封鎖，整個應用程式就必須等候。</span><span class="sxs-lookup"><span data-stu-id="b8382-112">If such an activity is blocked in a synchronous process, the entire application must wait.</span></span> <span data-ttu-id="b8382-113">在非同步處理序中，應用程式可以繼續處理其他與 Web 資源不相關的工作，直到可能的封鎖工作完成。</span><span class="sxs-lookup"><span data-stu-id="b8382-113">In an asynchronous process, the application can continue with other work that doesn't depend on the web resource until the potentially blocking task finishes.</span></span>  
  
 <span data-ttu-id="b8382-114">下表顯示非同步程式設計一般會改善回應速度的部分。</span><span class="sxs-lookup"><span data-stu-id="b8382-114">The following table shows typical areas where asynchronous programming improves responsiveness.</span></span> <span data-ttu-id="b8382-115">從 .NET 和 Windows 執行階段列出的 API 包含支援非同步程式設計的方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-115">The listed APIs from .NET and the Windows Runtime contain methods that support async programming.</span></span>  
  
| <span data-ttu-id="b8382-116">應用程式區域</span><span class="sxs-lookup"><span data-stu-id="b8382-116">Application area</span></span>    | <span data-ttu-id="b8382-117">使用非同步方法的 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="b8382-117">.NET types with async methods</span></span>     | <span data-ttu-id="b8382-118">使用非同步方法的 Windows 執行階段類型</span><span class="sxs-lookup"><span data-stu-id="b8382-118">Windows Runtime types with async methods</span></span>  |
|---------------------|-----------------------------------|-------------------------------------------|
|<span data-ttu-id="b8382-119">Web 存取</span><span class="sxs-lookup"><span data-stu-id="b8382-119">Web access</span></span>|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|<span data-ttu-id="b8382-120">處理檔案</span><span class="sxs-lookup"><span data-stu-id="b8382-120">Working with files</span></span>|<span data-ttu-id="b8382-121"><xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader></span><span class="sxs-lookup"><span data-stu-id="b8382-121"><xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader></span></span>|<xref:Windows.Storage.StorageFile>|  
|<span data-ttu-id="b8382-122">處理影像</span><span class="sxs-lookup"><span data-stu-id="b8382-122">Working with images</span></span>||<span data-ttu-id="b8382-123"><xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder></span><span class="sxs-lookup"><span data-stu-id="b8382-123"><xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder></span></span>|  
|<span data-ttu-id="b8382-124">WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="b8382-124">WCF programming</span></span>|[<span data-ttu-id="b8382-125">同步和非同步作業</span><span class="sxs-lookup"><span data-stu-id="b8382-125">Synchronous and Asynchronous Operations</span></span>](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
<span data-ttu-id="b8382-126">非同步對於存取 UI 執行緒的應用程式而言確實特別有用，因為所有 UI 相關活動通常都會共用一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="b8382-126">Asynchrony proves especially valuable for applications that access the UI thread because all UI-related activity usually shares one thread.</span></span> <span data-ttu-id="b8382-127">如果同步應用程式中有任何處理序遭到封鎖，所有處理序都會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="b8382-127">If any process is blocked in a synchronous application, all are blocked.</span></span> <span data-ttu-id="b8382-128">您的應用程式會停止回應，而且您可能會認為應用程式失敗，但實際上只是在等候。</span><span class="sxs-lookup"><span data-stu-id="b8382-128">Your application stops responding, and you might conclude that it has failed when instead it's just waiting.</span></span>  
  
 <span data-ttu-id="b8382-129">當您使用非同步方法時，應用程式會繼續回應 UI。</span><span class="sxs-lookup"><span data-stu-id="b8382-129">When you use asynchronous methods, the application continues to respond to the UI.</span></span> <span data-ttu-id="b8382-130">例如，您可以調整視窗大小或將視窗縮到最小，如果不想要等待應用程式完成，也可以將它關閉。</span><span class="sxs-lookup"><span data-stu-id="b8382-130">You can resize or minimize a window, for example, or you can close the application if you don't want to wait for it to finish.</span></span>  
  
 <span data-ttu-id="b8382-131">非同步方法會在設計非同步作業時，於選項清單中加入自動傳輸的對等項目讓您選擇。</span><span class="sxs-lookup"><span data-stu-id="b8382-131">The async-based approach adds the equivalent of an automatic transmission to the list of options that you can choose from when designing asynchronous operations.</span></span> <span data-ttu-id="b8382-132">也就是說，除了擁有傳統非同步程式設計的所有優點之外，開發人員所需投入的時間也大為減少。</span><span class="sxs-lookup"><span data-stu-id="b8382-132">That is, you get all the benefits of traditional asynchronous programming but with much less effort from the developer.</span></span>  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> <span data-ttu-id="b8382-133">非同步方法比較容易撰寫</span><span class="sxs-lookup"><span data-stu-id="b8382-133">Async methods are easier to write</span></span>  
 <span data-ttu-id="b8382-134">C# 中的 [async](../../../../csharp/language-reference/keywords/async.md) 和 [await](../../../../csharp/language-reference/keywords/await.md) 關鍵字都是非同步程式設計的核心。</span><span class="sxs-lookup"><span data-stu-id="b8382-134">The [async](../../../../csharp/language-reference/keywords/async.md) and [await](../../../../csharp/language-reference/keywords/await.md) keywords in C# are the heart of async programming.</span></span> <span data-ttu-id="b8382-135">您可以使用這兩個關鍵字，使用 .NET Framework、.NET Core 或 Windows 執行階段中的資源來建立非同步方法，幾乎就像建立同步方法一樣容易。</span><span class="sxs-lookup"><span data-stu-id="b8382-135">By using those two keywords, you can use resources in the .NET Framework, .NET Core, or the Windows Runtime to create an asynchronous method almost as easily as you create a synchronous method.</span></span> <span data-ttu-id="b8382-136">使用 `async` 關鍵字的非同步方法就稱為*非同步方法*。</span><span class="sxs-lookup"><span data-stu-id="b8382-136">Asynchronous methods that you define by using the `async` keyword are referred to as *async methods*.</span></span>  
  
 <span data-ttu-id="b8382-137">下列範例將示範非同步方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-137">The following example shows an async method.</span></span> <span data-ttu-id="b8382-138">程式碼中的一切對您而言應該幾乎完全熟悉。</span><span class="sxs-lookup"><span data-stu-id="b8382-138">Almost everything in the code should look completely familiar to you.</span></span> <span data-ttu-id="b8382-139">註解會標註您加入以建立非同步的功能。</span><span class="sxs-lookup"><span data-stu-id="b8382-139">The comments call out the features that you add to create the asynchrony.</span></span>  
  
 <span data-ttu-id="b8382-140">您可以在本主題結尾找到完整的 Windows Presentation Foundation (WPF) 範例檔案，並且可從[非同步範例：＜使用 Async 和 Await 進行非同步程式設計＞中的範例 (英文)](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c) 下載範例。</span><span class="sxs-lookup"><span data-stu-id="b8382-140">You can find a complete Windows Presentation Foundation (WPF) example file at the end of this topic, and you can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).</span></span>  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    HttpClient client = new HttpClient();  
  
    // GetStringAsync returns a Task<string>. That means that when you await the  
    // task you'll get a string (urlContents).  
    Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
    // You can do work here that doesn't rely on the string from GetStringAsync.  
    DoIndependentWork();  
  
    // The await operator suspends AccessTheWebAsync.  
    //  - AccessTheWebAsync can't continue until getStringTask is complete.  
    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
    //  - Control resumes here when getStringTask is complete.   
    //  - The await operator then retrieves the string result from getStringTask.  
    string urlContents = await getStringTask;  
  
    // The return statement specifies an integer result.  
    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="b8382-141">如果 `AccessTheWebAsync` 在呼叫 `GetStringAsync` 與等候其完成之間沒有任何可以執行的工作，您可以在下列單一陳述式中呼叫和等候，以簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="b8382-141">If `AccessTheWebAsync` doesn't have any work that it can do between calling `GetStringAsync` and awaiting its completion, you can simplify your code by calling and awaiting in the following single statement.</span></span>  
  
```csharp  
string urlContents = await client.GetStringAsync();  
```  
 
<span data-ttu-id="b8382-142">下列特性摘要說明上述範例為非同步方法的原因。</span><span class="sxs-lookup"><span data-stu-id="b8382-142">The following characteristics summarize what makes the previous example an async method.</span></span>  
  
-   <span data-ttu-id="b8382-143">方法簽章包含 `async` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b8382-143">The method signature includes an `async` modifier.</span></span>  
  
-   <span data-ttu-id="b8382-144">按照慣例，非同步方法的名稱是以 "Async" 後置字元為結尾。</span><span class="sxs-lookup"><span data-stu-id="b8382-144">The name of an async method, by convention, ends with an "Async" suffix.</span></span>  
  
-   <span data-ttu-id="b8382-145">傳回類型是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="b8382-145">The return type is one of the following types:</span></span>  
  
    -   <span data-ttu-id="b8382-146">如果方法的 return 陳述式中運算元的類型為 `TResult`，則為 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="b8382-146"><xref:System.Threading.Tasks.Task%601> if your method has a return statement in which the operand has type `TResult`.</span></span>  
  
    -   <span data-ttu-id="b8382-147">如果方法沒有 return 陳述式或是 return 陳述式沒有運算元，則為 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="b8382-147"><xref:System.Threading.Tasks.Task> if your method has no return statement or has a return statement with no operand.</span></span>  
  
    -   <span data-ttu-id="b8382-148">如果您撰寫的是非同步事件處理常式，則為 `void`。</span><span class="sxs-lookup"><span data-stu-id="b8382-148">`void` if you're writing an async event handler.</span></span>  

    -   <span data-ttu-id="b8382-149">任何具有 `GetAwaiter` 方法的其他類型 (從 C# 7 開始)。</span><span class="sxs-lookup"><span data-stu-id="b8382-149">Any other type that has a `GetAwaiter` method (starting with C# 7).</span></span>
  
     <span data-ttu-id="b8382-150">如需詳細資訊，請參閱[傳回型別和參數](#BKMK_ReturnTypesandParameters)一節。</span><span class="sxs-lookup"><span data-stu-id="b8382-150">For more information, see the [Return Types and Parameters](#BKMK_ReturnTypesandParameters) section.</span></span>  
  
-   <span data-ttu-id="b8382-151">方法通常至少包含一個 await 運算式，表示方法在等候的非同步作業完成後才能繼續的點。</span><span class="sxs-lookup"><span data-stu-id="b8382-151">The method usually includes at least one await expression, which marks a point where the method can't continue until the awaited asynchronous operation is complete.</span></span> <span data-ttu-id="b8382-152">此時，方法已暫停，而且控制權返回到方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b8382-152">In the meantime, the method is suspended, and control returns to the method's caller.</span></span> <span data-ttu-id="b8382-153">本主題的下一節將說明暫停點會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="b8382-153">The next section of this topic illustrates what happens at the suspension point.</span></span>  
  
 <span data-ttu-id="b8382-154">在非同步方法中，您會使用提供的關鍵字和類型表示您想要執行的工作，而編譯器會完成其餘的部分，包括追蹤控制權返回已暫停方法中的等候點時必須進行的作業。</span><span class="sxs-lookup"><span data-stu-id="b8382-154">In async methods, you use the provided keywords and types to indicate what you want to do, and the compiler does the rest, including keeping track of what must happen when control returns to an await point in a suspended method.</span></span> <span data-ttu-id="b8382-155">某些常式處理序像是迴圈和例外狀況處理，在傳統非同步程式碼中可能不容易處理。</span><span class="sxs-lookup"><span data-stu-id="b8382-155">Some routine processes, such as loops and exception handling, can be difficult to handle in traditional asynchronous code.</span></span> <span data-ttu-id="b8382-156">在非同步方法中，您可以像在同步方案中一樣撰寫這些項目，如此就可以解決這個問題了。</span><span class="sxs-lookup"><span data-stu-id="b8382-156">In an async method, you write these elements much as you would in a synchronous solution, and the problem is solved.</span></span>  
  
 <span data-ttu-id="b8382-157">如需舊版 .NET Framework 中非同步的詳細資訊，請參閱 [TPL 和傳統 .NET Framework 非同步程式設計](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="b8382-157">For more information about asynchrony in previous versions of the .NET Framework, see [TPL and Traditional .NET Framework Asynchronous Programming](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).</span></span>  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> <span data-ttu-id="b8382-158">非同步方法中執行了哪些工作</span><span class="sxs-lookup"><span data-stu-id="b8382-158">What happens in an async method</span></span>  
 <span data-ttu-id="b8382-159">在非同步程式設計中要了解的最重要事情，就是控制流程如何在方法之間移動。</span><span class="sxs-lookup"><span data-stu-id="b8382-159">The most important thing to understand in asynchronous programming is how the control flow moves from method to method.</span></span> <span data-ttu-id="b8382-160">下圖將引導您了解整個程序。</span><span class="sxs-lookup"><span data-stu-id="b8382-160">The following diagram leads you through the process.</span></span>  
  
 <span data-ttu-id="b8382-161">![追蹤非同步程式](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")</span><span class="sxs-lookup"><span data-stu-id="b8382-161">![Trace an async program](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")</span></span>  
  
 <span data-ttu-id="b8382-162">圖中的數字對應下列步驟。</span><span class="sxs-lookup"><span data-stu-id="b8382-162">The numbers in the diagram correspond to the following steps.</span></span>  
  
1.  <span data-ttu-id="b8382-163">事件處理常式會呼叫並等候 `AccessTheWebAsync` 非同步方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-163">An event handler calls and awaits the  `AccessTheWebAsync` async method.</span></span>  
  
2.  <span data-ttu-id="b8382-164">`AccessTheWebAsync` 會建立 <xref:System.Net.Http.HttpClient> 執行個體並呼叫 <xref:System.Net.Http.HttpClient.GetStringAsync%2A> 非同步方法，將網站的內容當做字串下載。</span><span class="sxs-lookup"><span data-stu-id="b8382-164">`AccessTheWebAsync` creates an <xref:System.Net.Http.HttpClient> instance and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2A> asynchronous method to download the contents of a website as a string.</span></span>  
  
3.  <span data-ttu-id="b8382-165">`GetStringAsync` 中發生了導致進度暫停的一些狀況。</span><span class="sxs-lookup"><span data-stu-id="b8382-165">Something happens in `GetStringAsync` that suspends its progress.</span></span> <span data-ttu-id="b8382-166">可能必須等待網站下載或其他封鎖活動。</span><span class="sxs-lookup"><span data-stu-id="b8382-166">Perhaps it must wait for a website to download or some other blocking activity.</span></span> <span data-ttu-id="b8382-167">為了避免封鎖資源，`GetStringAsync` 會將控制權遞交 (Yield) 給它的呼叫端 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="b8382-167">To avoid blocking resources, `GetStringAsync` yields control to its caller, `AccessTheWebAsync`.</span></span>  
  
     <span data-ttu-id="b8382-168">`GetStringAsync` 會傳回 <xref:System.Threading.Tasks.Task%601> (其中 `TResult` 是字串)，而 `AccessTheWebAsync` 則會將工作指派給 `getStringTask` 變數。</span><span class="sxs-lookup"><span data-stu-id="b8382-168">`GetStringAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is a string, and `AccessTheWebAsync` assigns the task to the `getStringTask` variable.</span></span> <span data-ttu-id="b8382-169">工作代表對 `GetStringAsync` 之呼叫的進行中程序，並承諾會在工作完成時產生實際字串值。</span><span class="sxs-lookup"><span data-stu-id="b8382-169">The task represents the ongoing process for the call to `GetStringAsync`, with a commitment to produce an actual string value when the work is complete.</span></span>  
  
4.  <span data-ttu-id="b8382-170">因為尚未等候 `getStringTask`，所以 `AccessTheWebAsync` 可以繼續進行其他不相依於 `GetStringAsync` 之最終結果的其他工作。</span><span class="sxs-lookup"><span data-stu-id="b8382-170">Because `getStringTask` hasn't been awaited yet, `AccessTheWebAsync` can continue with other work that doesn't depend on the final result from `GetStringAsync`.</span></span> <span data-ttu-id="b8382-171">這項工作是由對同步方法 `DoIndependentWork` 的呼叫來表示。</span><span class="sxs-lookup"><span data-stu-id="b8382-171">That work is represented by a call to the synchronous method `DoIndependentWork`.</span></span>  
  
5.  <span data-ttu-id="b8382-172">`DoIndependentWork` 是完成其工作並傳回其呼叫端的同步方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-172">`DoIndependentWork` is a synchronous method that does its work and returns to its caller.</span></span>  
  
6.  <span data-ttu-id="b8382-173">`AccessTheWebAsync` 已完成所有可處理的工作，但未取得來自 `getStringTask` 的結果。</span><span class="sxs-lookup"><span data-stu-id="b8382-173">`AccessTheWebAsync` has run out of work that it can do without a result from `getStringTask`.</span></span> <span data-ttu-id="b8382-174">`AccessTheWebAsync` 接著要計算和傳回下載字串的長度，但是方法必須等到有字串時才能計算該值。</span><span class="sxs-lookup"><span data-stu-id="b8382-174">`AccessTheWebAsync` next wants to calculate and return the length of the downloaded string, but the method can't calculate that value until the method has the string.</span></span>  
  
     <span data-ttu-id="b8382-175">因此，`AccessTheWebAsync` 會使用 await 運算子暫停其進度，並將控制權遞交 (Yield) 給呼叫 `AccessTheWebAsync` 的方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-175">Therefore, `AccessTheWebAsync` uses an await operator to suspend its progress and to yield control to the method that called `AccessTheWebAsync`.</span></span> <span data-ttu-id="b8382-176">`AccessTheWebAsync` 會將 `Task<int>` 傳回呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b8382-176">`AccessTheWebAsync` returns a `Task<int>` to the caller.</span></span> <span data-ttu-id="b8382-177">這項工作代表承諾會產生相當於下載字串長度的整數結果。</span><span class="sxs-lookup"><span data-stu-id="b8382-177">The task represents a promise to produce an integer result that's the length of the downloaded string.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8382-178">如果 `GetStringAsync` (和 `getStringTask`) 在 `AccessTheWebAsync` 等候它之前先完成，控制權仍會留在 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="b8382-178">If `GetStringAsync` (and therefore `getStringTask`) is complete before `AccessTheWebAsync` awaits it, control remains in `AccessTheWebAsync`.</span></span> <span data-ttu-id="b8382-179">如果呼叫的非同步處理序 (`getStringTask`) 已完成，而 `AccessTheWebSync` 無需等候最終結果時，那麼暫停然後再返回 `AccessTheWebAsync` 就是不必要的。</span><span class="sxs-lookup"><span data-stu-id="b8382-179">The expense of suspending and then returning to `AccessTheWebAsync` would be wasted if the called asynchronous process (`getStringTask`) has already completed and `AccessTheWebSync` doesn't have to wait for the final result.</span></span>  
  
     <span data-ttu-id="b8382-180">在呼叫端 (在這個範例中是事件處理常式) 內，處理模式會持續進行。</span><span class="sxs-lookup"><span data-stu-id="b8382-180">Inside the caller (the event handler in this example), the processing pattern continues.</span></span> <span data-ttu-id="b8382-181">呼叫端可能會在等候結果之前執行其他不取決於 `AccessTheWebAsync` 之結果的工作，或者呼叫端可能立即等候。</span><span class="sxs-lookup"><span data-stu-id="b8382-181">The caller might do other work that doesn't depend on the result from `AccessTheWebAsync` before awaiting that result, or the caller might await immediately.</span></span>   <span data-ttu-id="b8382-182">事件處理常式會等候 `AccessTheWebAsync`，而 `AccessTheWebAsync` 會等候 `GetStringAsync`。</span><span class="sxs-lookup"><span data-stu-id="b8382-182">The event handler is waiting for `AccessTheWebAsync`, and `AccessTheWebAsync` is waiting for `GetStringAsync`.</span></span>  
  
7.  <span data-ttu-id="b8382-183">`GetStringAsync` 完成並產生字串結果。</span><span class="sxs-lookup"><span data-stu-id="b8382-183">`GetStringAsync` completes and produces a string result.</span></span> <span data-ttu-id="b8382-184">字串結果不會依照您預期的方式透過呼叫 `GetStringAsync` 來傳回 </span><span class="sxs-lookup"><span data-stu-id="b8382-184">The string result isn't returned by the call to `GetStringAsync` in the way that you might expect.</span></span> <span data-ttu-id="b8382-185">(請記住，這個方法已在步驟 3 傳回工作)。字串結果會改為儲存在表示方法 `getStringTask` 完成的工作中。</span><span class="sxs-lookup"><span data-stu-id="b8382-185">(Remember that the method already returned a task in step 3.) Instead, the string result is stored in the task that represents the completion of the method, `getStringTask`.</span></span> <span data-ttu-id="b8382-186">await 運算子會從 `getStringTask` 擷取結果。</span><span class="sxs-lookup"><span data-stu-id="b8382-186">The await operator retrieves the result from `getStringTask`.</span></span> <span data-ttu-id="b8382-187">指派陳述式會將擷取的結果指派給 `urlContents`。</span><span class="sxs-lookup"><span data-stu-id="b8382-187">The assignment statement assigns the retrieved result to `urlContents`.</span></span>  
  
8.  <span data-ttu-id="b8382-188">當 `AccessTheWebAsync` 擁有字串結果時，方法就可以計算字串的長度。</span><span class="sxs-lookup"><span data-stu-id="b8382-188">When `AccessTheWebAsync` has the string result, the method can calculate the length of the string.</span></span> <span data-ttu-id="b8382-189">然後 `AccessTheWebAsync` 的工作也已完成，而且等候事件處理常式可以繼續執行。</span><span class="sxs-lookup"><span data-stu-id="b8382-189">Then the work of `AccessTheWebAsync` is also complete, and the waiting event handler can resume.</span></span> <span data-ttu-id="b8382-190">在本主題最後的完整範例中，您可以確認事件處理常式會擷取並列印長度結果的值。</span><span class="sxs-lookup"><span data-stu-id="b8382-190">In the full example at the end of the topic, you can confirm that the event handler retrieves and prints the value of the length result.</span></span>    
<span data-ttu-id="b8382-191">如果您不熟悉非同步程式設計，請花一分鐘思考同步和非同步行為之間的差異。</span><span class="sxs-lookup"><span data-stu-id="b8382-191">If you are new to asynchronous programming, take a minute to consider the difference between synchronous and asynchronous behavior.</span></span> <span data-ttu-id="b8382-192">同步方法會在其工作完成時傳回 (步驟 5)，而非同步方法則會在其工作暫停時傳回工作值 (步驟 3 和步驟 6)。</span><span class="sxs-lookup"><span data-stu-id="b8382-192">A synchronous method returns when its work is complete (step 5), but an async method returns a task value when its work is suspended (steps 3 and 6).</span></span> <span data-ttu-id="b8382-193">當非同步方法最後完成其工作時，工作會標示為已完成，而結果 (如果有的話) 會儲存在工作中。</span><span class="sxs-lookup"><span data-stu-id="b8382-193">When the async method eventually completes its work, the task is marked as completed and the result, if any, is stored in the task.</span></span>  
  
<span data-ttu-id="b8382-194">如需控制流程的詳細資訊，請參閱[非同步程式中的控制流程 (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)。</span><span class="sxs-lookup"><span data-stu-id="b8382-194">For more information about control flow, see [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
##  <a name="BKMK_APIAsyncMethods"></a> <span data-ttu-id="b8382-195">API 非同步方法</span><span class="sxs-lookup"><span data-stu-id="b8382-195">API async methods</span></span>  
 <span data-ttu-id="b8382-196">您可能會想知道哪裡可以找到支援非同步程式設計的方法，例如 `GetStringAsync`。</span><span class="sxs-lookup"><span data-stu-id="b8382-196">You might be wondering where to find methods such as `GetStringAsync` that support async programming.</span></span> <span data-ttu-id="b8382-197">.NET Framework 4.5 或更新版本以及 .NET Core 包含許多使用 `async` 和 `await` 的成員。</span><span class="sxs-lookup"><span data-stu-id="b8382-197">The  .NET Framework 4.5 or higher and .NET Core contain many members that work with `async` and `await`.</span></span> <span data-ttu-id="b8382-198">您也可以透過附加至成員名稱的 "Async" 後置字元以及傳回型別 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 來進行辨識。</span><span class="sxs-lookup"><span data-stu-id="b8382-198">You can recognize them by the "Async" suffix that’s appended to the member name, and by their return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b8382-199">例如，相對於同步方法 <xref:System.IO.Stream.CopyTo%2A>、<xref:System.IO.Stream.Read%2A> 和 <xref:System.IO.Stream.Write%2A>，`System.IO.Stream` 類別也包含一些方法，例如 <xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="b8382-199">For example, the `System.IO.Stream` class contains methods such as <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> alongside the synchronous methods <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, and <xref:System.IO.Stream.Write%2A>.</span></span>  
  
 <span data-ttu-id="b8382-200">Windows 執行階段也包含許多您可以在 Windows 應用程式中與 `async` 和 `await` 搭配使用的方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-200">The Windows Runtime also contains many methods that you can use with `async` and `await` in Windows apps.</span></span> <span data-ttu-id="b8382-201">如需詳細資訊，請參閱適用於 UWP 開發的[執行緒和非同步程式設計](/windows/uwp/threading-async/)，如果您使用舊版的 Windows 執行階段，則請參閱[非同步程式設計 (Windows 市集應用程式)](/previous-versions/windows/apps/hh464924(v=win.10)) 和[快速入門：使用 await 運算子進行非同步程式設計](/previous-versions/windows/apps/hh452713(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="b8382-201">For more information, see [Threading and async programming](/windows/uwp/threading-async/) for UWP development, and [Asynchronous programming (Windows Store apps)](/previous-versions/windows/apps/hh464924(v=win.10)) and [Quickstart: using the await operator for asynchronous programming](/previous-versions/windows/apps/hh452713(v=win.10)) if you use earlier versions of the Windows Runtime.</span></span>  
  
##  <a name="BKMK_Threads"></a> <span data-ttu-id="b8382-202">執行緒</span><span class="sxs-lookup"><span data-stu-id="b8382-202">Threads</span></span>  
<span data-ttu-id="b8382-203">非同步方法主要做為非封鎖作業使用。</span><span class="sxs-lookup"><span data-stu-id="b8382-203">Async methods are intended to be non-blocking operations.</span></span> <span data-ttu-id="b8382-204">當等候的工作正在執行時，非同步方法的 `await` 運算式不會封鎖目前的執行緒。</span><span class="sxs-lookup"><span data-stu-id="b8382-204">An `await` expression in an async method doesn’t block the current thread while the awaited task is running.</span></span> <span data-ttu-id="b8382-205">運算式會改為註冊方法的其餘部分做為接續，並將控制權交還給非同步方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b8382-205">Instead, the expression signs up the rest of the method as a continuation and returns control to the caller of the async method.</span></span>  
  
<span data-ttu-id="b8382-206">`async` 和 `await` 關鍵字不會導致建立其他執行緒。</span><span class="sxs-lookup"><span data-stu-id="b8382-206">The `async` and `await` keywords don't cause additional threads to be created.</span></span> <span data-ttu-id="b8382-207">由於非同步方法不會在本身的執行緒上執行，因此非同步方法不需要多執行緒。</span><span class="sxs-lookup"><span data-stu-id="b8382-207">Async methods don't require multithreading because an async method doesn't run on its own thread.</span></span> <span data-ttu-id="b8382-208">方法會在目前的同步處理內容執行，而且只有在方法為作用中時才會在執行緒上花費時間。</span><span class="sxs-lookup"><span data-stu-id="b8382-208">The method runs on the current synchronization context and uses time on the thread only when the method is active.</span></span> <span data-ttu-id="b8382-209">您可以使用 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 將受限於 CPU 的工作移到背景執行緒，但是背景執行緒無法協助處理正在等待結果產生的處理序。</span><span class="sxs-lookup"><span data-stu-id="b8382-209">You can use <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> to move CPU-bound work to a background thread, but a background thread doesn't help with a process that's just waiting for results to become available.</span></span>  
  
<span data-ttu-id="b8382-210">非同步程式設計的非同步方法幾乎是所有案例的現有方法當中較好的方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-210">The async-based approach to asynchronous programming is preferable to existing approaches in almost every case.</span></span> <span data-ttu-id="b8382-211">特別是，這個方法比受限於 IO 作業的 <xref:System.ComponentModel.BackgroundWorker> 類別還要好，因為程式碼較簡單，而且不需要防範競爭情況。</span><span class="sxs-lookup"><span data-stu-id="b8382-211">In particular, this approach is better than the <xref:System.ComponentModel.BackgroundWorker> class for IO-bound operations because the code is simpler and you don't have to guard against race conditions.</span></span> <span data-ttu-id="b8382-212">與 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 方法結合時，非同步程式設計會比受限於 CPU 作業的 <xref:System.ComponentModel.BackgroundWorker> 還要好，因為非同步程式設計會將執行程式碼的協調工作細節，從 `Task.Run` 傳輸至執行緒集區的工作中分出來。</span><span class="sxs-lookup"><span data-stu-id="b8382-212">In combination with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method, async programming is better than <xref:System.ComponentModel.BackgroundWorker> for CPU-bound operations because async programming separates the coordination details of running your code from the work that `Task.Run` transfers to the threadpool.</span></span>  
  
##  <a name="BKMK_AsyncandAwait"></a> <span data-ttu-id="b8382-213">async 和 await</span><span class="sxs-lookup"><span data-stu-id="b8382-213">async and await</span></span>  
 <span data-ttu-id="b8382-214">如果您使用 [async](../../../../csharp/language-reference/keywords/async.md) 修飾詞來將方法指定為非同步方法，就會啟用下列兩項功能。</span><span class="sxs-lookup"><span data-stu-id="b8382-214">If you specify that a method is an async method by using the [async](../../../../csharp/language-reference/keywords/async.md) modifier, you enable the following two capabilities.</span></span>  
  
-   <span data-ttu-id="b8382-215">標記的非同步方法可以使用 [await](../../../../csharp/language-reference/keywords/await.md) 來指定暫停點。</span><span class="sxs-lookup"><span data-stu-id="b8382-215">The marked async method can use [await](../../../../csharp/language-reference/keywords/await.md) to designate suspension points.</span></span> <span data-ttu-id="b8382-216">`await` 運算子會告知編譯器，非同步方法只有在等候的非同步處理序完成後，才能繼續通過該點。</span><span class="sxs-lookup"><span data-stu-id="b8382-216">The `await` operator tells the compiler that the async method can't continue past that point until the awaited asynchronous process is complete.</span></span> <span data-ttu-id="b8382-217">同時，控制權會返回非同步方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b8382-217">In the meantime, control returns to the caller of the async method.</span></span>  
  
     <span data-ttu-id="b8382-218">非同步方法在 `await` 運算式上暫停時，並不構成從方法退出，而 `finally` 區塊也不會執行。</span><span class="sxs-lookup"><span data-stu-id="b8382-218">The suspension of an async method at an `await` expression doesn't constitute an exit from the method, and `finally` blocks don’t run.</span></span>  
  
-   <span data-ttu-id="b8382-219">標記的非同步方法本身可以做為其呼叫方法的等候目標。</span><span class="sxs-lookup"><span data-stu-id="b8382-219">The marked async method can itself be awaited by methods that call it.</span></span>  
  
<span data-ttu-id="b8382-220">非同步方法中通常會出現一或多次 `await` 運算子，但是沒有 `await` 運算式也不會造成編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="b8382-220">An async method typically contains one or more occurrences of an `await` operator, but the absence of `await` expressions doesn’t cause a compiler error.</span></span> <span data-ttu-id="b8382-221">如果非同步方法未使用 `await` 運算子來標記暫停點，方法會無視於 `async` 修飾詞，像同步方法一樣執行。</span><span class="sxs-lookup"><span data-stu-id="b8382-221">If an async method doesn’t use an `await` operator to mark a suspension point, the method executes as a synchronous method does, despite the `async` modifier.</span></span> <span data-ttu-id="b8382-222">編譯器將對這類方法發出警告。</span><span class="sxs-lookup"><span data-stu-id="b8382-222">The compiler issues a warning for such methods.</span></span>  
  
 <span data-ttu-id="b8382-223">`async` 和 `await` 都是內容關鍵字。</span><span class="sxs-lookup"><span data-stu-id="b8382-223">`async` and `await` are contextual keywords.</span></span> <span data-ttu-id="b8382-224">如需詳細資訊和範例，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="b8382-224">For more information and examples, see the following topics:</span></span>  
  
-   [<span data-ttu-id="b8382-225">async</span><span class="sxs-lookup"><span data-stu-id="b8382-225">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
  
-   [<span data-ttu-id="b8382-226">await</span><span class="sxs-lookup"><span data-stu-id="b8382-226">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> <span data-ttu-id="b8382-227">傳回型別和參數</span><span class="sxs-lookup"><span data-stu-id="b8382-227">Return types and parameters</span></span>  
<span data-ttu-id="b8382-228">async 方法通常會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="b8382-228">An async method typically returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="b8382-229">在非同步方法內，會將 `await` 運算子套用到呼叫另一個非同步方法所傳回的工作。</span><span class="sxs-lookup"><span data-stu-id="b8382-229">Inside an async method, an `await` operator is applied to a task that's returned from a call to another async method.</span></span>  
  
<span data-ttu-id="b8382-230">如果方法包含指定 `TResult` 類型運算元的 [return](../../../../csharp/language-reference/keywords/return.md) 陳述式，請指定 <xref:System.Threading.Tasks.Task%601> 作為傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b8382-230">You specify <xref:System.Threading.Tasks.Task%601> as the return type if the method contains a [return](../../../../csharp/language-reference/keywords/return.md) statement that specifies an operand of type `TResult`.</span></span> 
  
<span data-ttu-id="b8382-231">如果方法沒有 return 陳述式，或者方法的 return 陳述式不會傳回運算元，請使用 <xref:System.Threading.Tasks.Task> 作為傳回型別。</span><span class="sxs-lookup"><span data-stu-id="b8382-231">You use <xref:System.Threading.Tasks.Task>  as the return type if the method has no return statement or has a return statement that doesn't return an operand.</span></span>  

<span data-ttu-id="b8382-232">從 C# 7 開始，您也可以指定任何其他傳回型別，前提是該類型包括 `GetAwaiter` 方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-232">Starting with C# 7, you can also specify any other return type, provided that that type includes a `GetAwaiter` method.</span></span> <span data-ttu-id="b8382-233">這類類型的範例是 <xref:System.Threading.Tasks.ValueTask%601>。</span><span class="sxs-lookup"><span data-stu-id="b8382-233"><xref:System.Threading.Tasks.ValueTask%601> is an example of such a type.</span></span> <span data-ttu-id="b8382-234">它提供於 [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet 套件中。</span><span class="sxs-lookup"><span data-stu-id="b8382-234">It is available in the [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet package.</span></span>
  
 <span data-ttu-id="b8382-235">下列範例將示範如何宣告和呼叫會傳回 <xref:System.Threading.Tasks.Task%601> 或 <xref:System.Threading.Tasks.Task> 的方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-235">The following example shows how you declare and call a method that returns a <xref:System.Threading.Tasks.Task%601> or a <xref:System.Threading.Tasks.Task>.</span></span>  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> TaskOfTResult_MethodAsync()  
{  
    int hours;  
    // . . .  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to TaskOfTResult_MethodAsync  
Task<int> returnedTaskTResult = TaskOfTResult_MethodAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await TaskOfTResult_MethodAsync();  
  
// Signature specifies Task  
async Task Task_MethodAsync()  
{  
    // . . .  
    // The method has no return statement.    
}  
  
// Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync();  
await returnedTask;  
// or, in a single statement  
await Task_MethodAsync();  
```  
  
<span data-ttu-id="b8382-236">每項傳回的工作都代表進行中的工作。</span><span class="sxs-lookup"><span data-stu-id="b8382-236">Each returned task represents ongoing work.</span></span> <span data-ttu-id="b8382-237">工作會封裝這個非同步處理序狀態的相關資訊，以及處理序的最終結果，或是處理序不成功時，則會封裝處理序引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8382-237">A task encapsulates information about the state of the asynchronous process and, eventually, either the final result from the process or the exception that the process raises if it doesn't succeed.</span></span>  
  
<span data-ttu-id="b8382-238">非同步方法的傳回型別也可以是 `void`。</span><span class="sxs-lookup"><span data-stu-id="b8382-238">An async method can also have a `void` return type.</span></span> <span data-ttu-id="b8382-239">這個傳回類型主要用於定義需要 `void` 傳回類型的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b8382-239">This return type is used primarily to define event handlers, where a `void` return type is required.</span></span> <span data-ttu-id="b8382-240">非同步事件處理常式通常做為非同步程式的起點。</span><span class="sxs-lookup"><span data-stu-id="b8382-240">Async event handlers often serve as the starting point for async programs.</span></span>  
  
<span data-ttu-id="b8382-241">無法等候傳回型別為 `void` 的非同步方法，而且傳回 void 的方法呼叫端無法攔截該方法擲回的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b8382-241">An async method that has a `void` return type can’t be awaited, and the caller of a void-returning method can't catch any exceptions that the method throws.</span></span>  
  
<span data-ttu-id="b8382-242">非同步方法無法宣告 [ref](../../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../../csharp/language-reference/keywords/out.md) 參數，但是此方法可以呼叫具有這類參數的方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-242">An async method can't declare [ref](../../../../csharp/language-reference/keywords/ref.md) or [out](../../../../csharp/language-reference/keywords/out.md) parameters, but the method can call methods that have such parameters.</span></span> <span data-ttu-id="b8382-243">同樣地，async 方法無法以傳址方式傳回值，但可以使用 ref 傳回值呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-243">Similarly, an async method can't return a value by reference, although it can call methods with ref return values.</span></span> 
  
<span data-ttu-id="b8382-244">如需詳細資訊和範例，請參閱[非同步傳回型別 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b8382-244">For more information and examples, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span> <span data-ttu-id="b8382-245">如需如何在非同步方法中攔截例外狀況的詳細資訊，請參閱 [try-catch](../../../../csharp/language-reference/keywords/try-catch.md)。</span><span class="sxs-lookup"><span data-stu-id="b8382-245">For more information about how to catch exceptions in async methods, see [try-catch](../../../../csharp/language-reference/keywords/try-catch.md).</span></span> 
  
<span data-ttu-id="b8382-246">Windows 執行階段程式設計中的非同步 API 具有下列其中一種傳回型別 (類似於工作)：</span><span class="sxs-lookup"><span data-stu-id="b8382-246">Asynchronous APIs in Windows Runtime programming have one of the following return types, which are similar to tasks:</span></span>  
  
-   <span data-ttu-id="b8382-247"><xref:Windows.Foundation.IAsyncOperation%601>，對應至 <xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="b8382-247"><xref:Windows.Foundation.IAsyncOperation%601>, which corresponds to <xref:System.Threading.Tasks.Task%601></span></span>  
  
-   <span data-ttu-id="b8382-248"><xref:Windows.Foundation.IAsyncAction>，對應至 <xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="b8382-248"><xref:Windows.Foundation.IAsyncAction>, which corresponds to <xref:System.Threading.Tasks.Task></span></span>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a> <span data-ttu-id="b8382-249">命名慣例</span><span class="sxs-lookup"><span data-stu-id="b8382-249">Naming convention</span></span>  
 <span data-ttu-id="b8382-250">依照慣例，您會將 "Async" 附加至具有 `async` 修飾詞的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="b8382-250">By convention, you append "Async" to the names of methods that have an `async` modifier.</span></span>  
  
 <span data-ttu-id="b8382-251">當事件、基底類別或介面合約採用不同的名稱時，您可以忽略慣例。</span><span class="sxs-lookup"><span data-stu-id="b8382-251">You can ignore the convention where an event, base class, or interface contract suggests a different name.</span></span> <span data-ttu-id="b8382-252">例如，您不應該重新命名通用事件處理常式，像是 `Button1_Click`。</span><span class="sxs-lookup"><span data-stu-id="b8382-252">For example, you shouldn’t rename common event handlers, such as `Button1_Click`.</span></span>  
  
##  <a name="BKMK_RelatedTopics"></a> <span data-ttu-id="b8382-253">相關主題和範例 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="b8382-253">Related topics and samples (Visual Studio)</span></span>  
  
|<span data-ttu-id="b8382-254">標題</span><span class="sxs-lookup"><span data-stu-id="b8382-254">Title</span></span>|<span data-ttu-id="b8382-255">描述</span><span class="sxs-lookup"><span data-stu-id="b8382-255">Description</span></span>|<span data-ttu-id="b8382-256">範例</span><span class="sxs-lookup"><span data-stu-id="b8382-256">Sample</span></span>|  
|-----------|-----------------|------------|  
|[<span data-ttu-id="b8382-257">逐步解說：使用 async 和 await 存取 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-257">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|<span data-ttu-id="b8382-258">顯示如何將同步 WPF 方案轉換為非同步 WPF 方案。</span><span class="sxs-lookup"><span data-stu-id="b8382-258">Shows how to convert a synchronous WPF solution to an asynchronous WPF solution.</span></span> <span data-ttu-id="b8382-259">應用程式會下載一系列的網站。</span><span class="sxs-lookup"><span data-stu-id="b8382-259">The application downloads a series of websites.</span></span>|[<span data-ttu-id="b8382-260">非同步範例：存取 Web 逐步解說 (英文)</span><span class="sxs-lookup"><span data-stu-id="b8382-260">Async Sample: Accessing the Web Walkthrough</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[<span data-ttu-id="b8382-261">如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-261">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|<span data-ttu-id="b8382-262">將 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 加入至前一個逐步解說。</span><span class="sxs-lookup"><span data-stu-id="b8382-262">Adds <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> to the previous walkthrough.</span></span> <span data-ttu-id="b8382-263">使用 `WhenAll` 會同時開始進行所有的下載。</span><span class="sxs-lookup"><span data-stu-id="b8382-263">The use of `WhenAll` starts all the downloads at the same time.</span></span>||  
|[<span data-ttu-id="b8382-264">如何：使用 async 和 await，同時發出多個 Web 要求 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-264">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|<span data-ttu-id="b8382-265">示範如何同時啟動數個工作。</span><span class="sxs-lookup"><span data-stu-id="b8382-265">Demonstrates how to start several tasks at the same time.</span></span>|[<span data-ttu-id="b8382-266">非同步範例：平行進行多個 Web 要求 (英文)</span><span class="sxs-lookup"><span data-stu-id="b8382-266">Async Sample: Make Multiple Web Requests in Parallel</span></span>](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[<span data-ttu-id="b8382-267">非同步方法的傳回型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-267">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|<span data-ttu-id="b8382-268">說明非同步方法可以傳回的類型，並解釋每種類型的適用時機。</span><span class="sxs-lookup"><span data-stu-id="b8382-268">Illustrates the types that async methods can return and explains when each type is appropriate.</span></span>||  
|[<span data-ttu-id="b8382-269">非同步程式中的控制流程 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-269">Control Flow in Async Programs (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|<span data-ttu-id="b8382-270">在非同步程式中詳細追蹤一連串 await 運算式的控制流程。</span><span class="sxs-lookup"><span data-stu-id="b8382-270">Traces in detail the flow of control through a succession of await expressions in an asynchronous program.</span></span>|[<span data-ttu-id="b8382-271">非同步範例：非同步程式中的控制流程 (英文)</span><span class="sxs-lookup"><span data-stu-id="b8382-271">Async Sample: Control Flow in Async Programs</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[<span data-ttu-id="b8382-272">微調非同步應用程式 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-272">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|<span data-ttu-id="b8382-273">顯示如何將下列功能加入至您的非同步方案：</span><span class="sxs-lookup"><span data-stu-id="b8382-273">Shows how to add the following functionality to your async solution:</span></span><br /><br /> <span data-ttu-id="b8382-274">-   [取消一項非同步工作或工作清單 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="b8382-274">-   [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)</span></span><br /><span data-ttu-id="b8382-275">-   [在一段時間後取消非同步工作 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)</span><span class="sxs-lookup"><span data-stu-id="b8382-275">-   [Cancel Async Tasks after a Period of Time (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)</span></span><br /><span data-ttu-id="b8382-276">-   [當其中一項非同步工作完成時，取消剩餘的非同步工作 (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)</span><span class="sxs-lookup"><span data-stu-id="b8382-276">-   [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)</span></span><br /><span data-ttu-id="b8382-277">-   [啟動多項非同步工作並在它們完成時進行處理 (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)</span><span class="sxs-lookup"><span data-stu-id="b8382-277">-   [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)</span></span>|[<span data-ttu-id="b8382-278">非同步範例：微調應用程式 (英文)</span><span class="sxs-lookup"><span data-stu-id="b8382-278">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[<span data-ttu-id="b8382-279">處理非同步應用程式中的重新進入 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-279">Handling Reentrancy in Async Apps (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|<span data-ttu-id="b8382-280">顯示如何處理現用非同步作業在執行當中重新啟動的情況。</span><span class="sxs-lookup"><span data-stu-id="b8382-280">Shows how to handle cases in which an active asynchronous operation is restarted while it’s running.</span></span>||  
|<span data-ttu-id="b8382-281">[WhenAny：銜接 .NET Framework 和 Windows 執行階段](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)</span><span class="sxs-lookup"><span data-stu-id="b8382-281">[WhenAny: Bridging between the .NET Framework and the Windows Runtime](https://msdn.microsoft.com/library/jj635140(v=vs.120).aspx)</span></span>|<span data-ttu-id="b8382-282">顯示如何在 [!INCLUDE[wrt](~/includes/wrt-md.md)] 中進行 .NET Framework 與 IAsyncOperations 之工作類型之間的橋接，讓您可以搭配使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 與 [!INCLUDE[wrt](~/includes/wrt-md.md)] 方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-282">Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the [!INCLUDE[wrt](~/includes/wrt-md.md)] so that you can use <xref:System.Threading.Tasks.Task.WhenAny%2A> with a [!INCLUDE[wrt](~/includes/wrt-md.md)] method.</span></span>|[<span data-ttu-id="b8382-283">非同步範例：銜接 .NET 和 Windows 執行階段 (AsTask 和 WhenAny) (英文)</span><span class="sxs-lookup"><span data-stu-id="b8382-283">Async Sample: Bridging between .NET and Windows Runtime (AsTask and WhenAny)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|<span data-ttu-id="b8382-284">非同步取消作業：銜接 .NET Framework 和 Windows 執行階段</span><span class="sxs-lookup"><span data-stu-id="b8382-284">Async Cancellation: Bridging between the .NET Framework and the Windows Runtime</span></span>|<span data-ttu-id="b8382-285">顯示如何在 [!INCLUDE[wrt](~/includes/wrt-md.md)] 中進行 .NET Framework 與 IAsyncOperations 的工作類型之間的橋接，讓您可以搭配使用 <xref:System.Threading.CancellationTokenSource> 與 [!INCLUDE[wrt](~/includes/wrt-md.md)] 方法。</span><span class="sxs-lookup"><span data-stu-id="b8382-285">Shows how to bridge between Task types in the .NET Framework and IAsyncOperations in the [!INCLUDE[wrt](~/includes/wrt-md.md)] so that you can use <xref:System.Threading.CancellationTokenSource> with a [!INCLUDE[wrt](~/includes/wrt-md.md)] method.</span></span>|[<span data-ttu-id="b8382-286">非同步範例：銜接 .NET 和 Windows 執行階段 (AsTask & Cancellation) (英文)</span><span class="sxs-lookup"><span data-stu-id="b8382-286">Async Sample: Bridging between .NET and Windows Runtime (AsTask & Cancellation)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[<span data-ttu-id="b8382-287">使用非同步功能存取檔案 (C#)</span><span class="sxs-lookup"><span data-stu-id="b8382-287">Using Async for File Access (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|<span data-ttu-id="b8382-288">列出並示範使用 async 和 await 存取檔案的優點。</span><span class="sxs-lookup"><span data-stu-id="b8382-288">Lists and demonstrates the benefits of using async and await to access files.</span></span>||  
|[<span data-ttu-id="b8382-289">工作式非同步模式 (TAP)</span><span class="sxs-lookup"><span data-stu-id="b8382-289">Task-based Asynchronous Pattern (TAP)</span></span>](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|<span data-ttu-id="b8382-290">描述 .NET Framework 中非同步的新模式。</span><span class="sxs-lookup"><span data-stu-id="b8382-290">Describes a new pattern for asynchrony in the .NET Framework.</span></span> <span data-ttu-id="b8382-291">這個模式是根據 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="b8382-291">The pattern is based on the <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> types.</span></span>||  
|[<span data-ttu-id="b8382-292">Channel 9 上的非同步影片</span><span class="sxs-lookup"><span data-stu-id="b8382-292">Async Videos on Channel 9</span></span>](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|<span data-ttu-id="b8382-293">提供有關非同步程式設計的各種不同視訊連結。</span><span class="sxs-lookup"><span data-stu-id="b8382-293">Provides links to a variety of videos about async programming.</span></span>||  
  
##  <a name="BKMK_CompleteExample"></a> <span data-ttu-id="b8382-294">完整範例</span><span class="sxs-lookup"><span data-stu-id="b8382-294">Complete example</span></span>  
 <span data-ttu-id="b8382-295">下列程式碼是本主題討論之 Windows Presentation Foundation (WPF) 應用程式中的 MainWindow.xaml.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8382-295">The following code is the MainWindow.xaml.cs file from the Windows Presentation Foundation (WPF) application that this topic discusses.</span></span> <span data-ttu-id="b8382-296">您可以從[非同步範例：＜使用 Async 和 Await 進行非同步程式設計＞中的範例 (英文)](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c) 下載範例。</span><span class="sxs-lookup"><span data-stu-id="b8382-296">You can download the sample from [Async Sample: Example from "Asynchronous Programming with Async and Await"](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http;  
using System.Net.Http;  
  
namespace AsyncFirstExample  
{  
    public partial class MainWindow : Window  
    {  
        // Mark the event handler with async so you can use await in it.  
        private async void StartButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Call and await separately.  
            //Task<int> getLengthTask = AccessTheWebAsync();  
            //// You can do independent work here.  
            //int contentLength = await getLengthTask;  
  
            int contentLength = await AccessTheWebAsync();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            HttpClient client = new HttpClient();  
  
            // GetStringAsync returns a Task<string>. That means that when you await the  
            // task you'll get a string (urlContents).  
            Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
            // You can do work here that doesn't rely on the string from GetStringAsync.  
            DoIndependentWork();  
  
            // The await operator suspends AccessTheWebAsync.  
            //  - AccessTheWebAsync can't continue until getStringTask is complete.  
            //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
            //  - Control resumes here when getStringTask is complete.   
            //  - The await operator then retrieves the string result from getStringTask.  
            string urlContents = await getStringTask;  
  
            // The return statement specifies an integer result.  
            // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
            return urlContents.Length;  
        }  
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 41564.  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8382-297">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8382-297">See also</span></span>  
 [<span data-ttu-id="b8382-298">async</span><span class="sxs-lookup"><span data-stu-id="b8382-298">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="b8382-299">await</span><span class="sxs-lookup"><span data-stu-id="b8382-299">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="b8382-300">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="b8382-300">Asynchronous programming</span></span>](../../../../csharp/async.md)  
 [<span data-ttu-id="b8382-301">非同步總覽</span><span class="sxs-lookup"><span data-stu-id="b8382-301">Async overview</span></span>](../../../../standard/async.md)  
