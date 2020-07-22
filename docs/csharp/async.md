---
title: 非同步程式設計 - C#
description: 深入了解 .NET Core 提供之 C# 語言層級的非同步程式設計模型。
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 35ba90f978b1993f80451a28a4cd08129afddd85
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864497"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="d0981-103">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="d0981-103">Asynchronous programming</span></span>

<span data-ttu-id="d0981-104">如果您有任何 i/o 系結的需求（例如，從網路要求資料、存取資料庫，或讀取和寫入檔案系統），您會想要利用非同步程式設計。</span><span class="sxs-lookup"><span data-stu-id="d0981-104">If you have any I/O-bound needs (such as requesting data from a network, accessing a database, or reading and writing to a file system), you'll want to utilize asynchronous programming.</span></span> <span data-ttu-id="d0981-105">您也可能會有 CPU 繫結程式碼，例如執行耗費資源的計算，這也是不錯的非同步程式碼撰寫案例。</span><span class="sxs-lookup"><span data-stu-id="d0981-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="d0981-106">C # 具有語言層級的非同步程式設計模型，可讓您輕鬆地撰寫非同步程式碼，而不需要操控回呼或符合支援非同步程式庫。</span><span class="sxs-lookup"><span data-stu-id="d0981-106">C# has a language-level asynchronous programming model, which allows for easily writing asynchronous code, without having to juggle callbacks or conform to a library that supports asynchrony.</span></span> <span data-ttu-id="d0981-107">它會遵循稱為[工作式非同步模式 (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) 的模式。</span><span class="sxs-lookup"><span data-stu-id="d0981-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="overview-of-the-asynchronous-model"></a><span data-ttu-id="d0981-108">非同步模型的總覽</span><span class="sxs-lookup"><span data-stu-id="d0981-108">Overview of the asynchronous model</span></span>

<span data-ttu-id="d0981-109">非同步程式設計的核心是建立非同步作業模型的 `Task` 和 `Task<T>` 物件。</span><span class="sxs-lookup"><span data-stu-id="d0981-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span> <span data-ttu-id="d0981-110">它們是受 `async` 和 `await` 關鍵字所支援。</span><span class="sxs-lookup"><span data-stu-id="d0981-110">They are supported by the `async` and `await` keywords.</span></span> <span data-ttu-id="d0981-111">在大部分情況下，模型都相當簡單︰</span><span class="sxs-lookup"><span data-stu-id="d0981-111">The model is fairly simple in most cases:</span></span>

- <span data-ttu-id="d0981-112">針對 i/o 系結程式碼，您會等候會傳回 `Task` 或 `Task<T>` 在方法內部的作業 `async` 。</span><span class="sxs-lookup"><span data-stu-id="d0981-112">For I/O-bound code, you await an operation that returns a `Task` or `Task<T>` inside of an `async` method.</span></span>
- <span data-ttu-id="d0981-113">針對 CPU 系結程式碼，您會使用方法，來等候在背景執行緒上啟動的作業 <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d0981-113">For CPU-bound code, you await an operation that is started on a background thread with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d0981-114">`await` 關鍵字就是顯現魔力的地方。</span><span class="sxs-lookup"><span data-stu-id="d0981-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="d0981-115">它會將控制交給執行 `await` 的方法呼叫端，最後讓 UI 有回應或服務有彈性。</span><span class="sxs-lookup"><span data-stu-id="d0981-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span> <span data-ttu-id="d0981-116">雖然[有方法](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)可以處理和以外的非同步程式碼，但本文 `async` `await` 的重點在於語言層級的結構。</span><span class="sxs-lookup"><span data-stu-id="d0981-116">While [there are ways](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) to approach async code other than `async` and `await`, this article focuses on the language-level constructs.</span></span>

### <a name="io-bound-example-download-data-from-a-web-service"></a><span data-ttu-id="d0981-117">I/o 系結範例：從 web 服務下載資料</span><span class="sxs-lookup"><span data-stu-id="d0981-117">I/O-bound example: Download data from a web service</span></span>

<span data-ttu-id="d0981-118">當按下按鈕時，您可能需要從 web 服務下載一些資料，但不想要封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="d0981-118">You may need to download some data from a web service when a button is pressed, but don't want to block the UI thread.</span></span> <span data-ttu-id="d0981-119">它可以如下完成：</span><span class="sxs-lookup"><span data-stu-id="d0981-119">It can be accomplished like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="d0981-120">此程式碼會表示意圖（以非同步方式下載資料），而不會向下很快與 `Task` 物件互動。</span><span class="sxs-lookup"><span data-stu-id="d0981-120">The code expresses the intent (downloading data asynchronously) without getting bogged down in interacting with `Task` objects.</span></span>

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a><span data-ttu-id="d0981-121">CPU 系結範例：執行遊戲的計算</span><span class="sxs-lookup"><span data-stu-id="d0981-121">CPU-bound example: Perform a calculation for a game</span></span>

<span data-ttu-id="d0981-122">假設您正在撰寫行動遊戲，而按下按鈕可能會損壞畫面上的許多敵人。</span><span class="sxs-lookup"><span data-stu-id="d0981-122">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span> <span data-ttu-id="d0981-123">執行損壞計算可能十分耗費資源，而且在 UI 執行緒上這麼做會讓遊戲似乎在執行計算時暫停！</span><span class="sxs-lookup"><span data-stu-id="d0981-123">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="d0981-124">處理這種情況的最佳方式是啟動背景執行緒，它會使用來執行工作 `Task.Run` ，並使用來等待其結果 `await` 。</span><span class="sxs-lookup"><span data-stu-id="d0981-124">The best way to handle this is to start a background thread, which does the work using `Task.Run`, and await its result using `await`.</span></span> <span data-ttu-id="d0981-125">這可讓 UI 在工作完成時感覺順暢。</span><span class="sxs-lookup"><span data-stu-id="d0981-125">This allows the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="d0981-126">此程式碼完全表示按鈕 click 事件的目的、不需要手動管理背景執行緒，並且以非封鎖方式這麼做。</span><span class="sxs-lookup"><span data-stu-id="d0981-126">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="d0981-127">背後作業</span><span class="sxs-lookup"><span data-stu-id="d0981-127">What happens under the covers</span></span>

<span data-ttu-id="d0981-128">其中有許多非同步作業的相關移動部分。</span><span class="sxs-lookup"><span data-stu-id="d0981-128">There are many moving pieces where asynchronous operations are concerned.</span></span> <span data-ttu-id="d0981-129">如果您想知道和背後的情況 `Task` `Task<T>` ，請參閱[非同步](../standard/async-in-depth.md)深入文章以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d0981-129">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, see the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="d0981-130">在 c # 方面，編譯器會將您的程式碼轉換成狀態機器，以追蹤在達到時執行的動作 `await` ，並在背景作業完成時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d0981-130">On the C# side of things, the compiler transforms your code into a state machine that keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="d0981-131">甚於理論上的需要，這是 [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises) (非同步的承諾模型) 的實作。</span><span class="sxs-lookup"><span data-stu-id="d0981-131">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="d0981-132">要瞭解的重要部分</span><span class="sxs-lookup"><span data-stu-id="d0981-132">Key pieces to understand</span></span>

* <span data-ttu-id="d0981-133">非同步程式碼可以用於 I/O 繫結和 CPU 繫結程式碼，但每個案例都不同。</span><span class="sxs-lookup"><span data-stu-id="d0981-133">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="d0981-134">非同步程式碼會使用 `Task<T>` 和 `Task`，這是用來在背景中完成建立工作模型的建構。</span><span class="sxs-lookup"><span data-stu-id="d0981-134">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="d0981-135">`async` 關鍵字會將方法轉換為非同步方法，讓您可以在其主體中使用 `await` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d0981-135">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="d0981-136">套用 `await` 關鍵字時，除非等候的工作完成，否則會暫止呼叫的方法，並將控制權返回其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="d0981-136">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="d0981-137">`await` 只能在非同步方法內使用。</span><span class="sxs-lookup"><span data-stu-id="d0981-137">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="d0981-138">辨識 CPU 系結和 i/o 系結工作</span><span class="sxs-lookup"><span data-stu-id="d0981-138">Recognize CPU-bound and I/O-bound work</span></span>

<span data-ttu-id="d0981-139">本手冊的前兩個範例示範如何使用 `async` 和 `await` 進行 I/O 繫結和 CPU 繫結工作。</span><span class="sxs-lookup"><span data-stu-id="d0981-139">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span> <span data-ttu-id="d0981-140">這是您識別所需執行的工作是 I/O 繫結還是 CPU 繫結的關鍵，因為它會大幅影響程式碼的效能，而且可能會導致誤用特定建構。</span><span class="sxs-lookup"><span data-stu-id="d0981-140">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="d0981-141">以下是您應該在撰寫任何程式碼之前提問的兩個問題︰</span><span class="sxs-lookup"><span data-stu-id="d0981-141">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="d0981-142">程式碼是否要「等候」什麼項目，例如資料庫中的資料？</span><span class="sxs-lookup"><span data-stu-id="d0981-142">Will your code be "waiting" for something, such as data from a database?</span></span>

   <span data-ttu-id="d0981-143">如果您的答案為「是」，則工作是 **I/O 繫結**。</span><span class="sxs-lookup"><span data-stu-id="d0981-143">If your answer is "yes", then your work is **I/O-bound**.</span></span>

1. <span data-ttu-id="d0981-144">您的程式碼會執行昂貴的計算嗎？</span><span class="sxs-lookup"><span data-stu-id="d0981-144">Will your code be performing an expensive computation?</span></span>

   <span data-ttu-id="d0981-145">如果您的答案為「是」，則工作是 **CPU 繫結**。</span><span class="sxs-lookup"><span data-stu-id="d0981-145">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="d0981-146">如果您的工作是「I/O 繫結」\*\*\*\*，請使用「沒有」`await` \*\* `Task.Run` 的 `async` 和 。</span><span class="sxs-lookup"><span data-stu-id="d0981-146">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span> <span data-ttu-id="d0981-147">您「不應該」\*\* 使用 Task Parallel Library。</span><span class="sxs-lookup"><span data-stu-id="d0981-147">You *should not* use the Task Parallel Library.</span></span> <span data-ttu-id="d0981-148">這項功能的原因會以[非同步方式](../standard/async-in-depth.md)概述。</span><span class="sxs-lookup"><span data-stu-id="d0981-148">The reason for this is outlined in [Async in Depth](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="d0981-149">如果您擁有的工作是**CPU**系結，而且您在意回應能力，請使用 `async` 和 `await` ，但使用在另一個執行緒*with*上衍生工作 `Task.Run` 。</span><span class="sxs-lookup"><span data-stu-id="d0981-149">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await`, but spawn off the work on another thread *with* `Task.Run`.</span></span> <span data-ttu-id="d0981-150">如果工作適用于並行和平行處理原則，也請考慮使用[Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="d0981-150">If the work is appropriate for concurrency and parallelism, also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="d0981-151">此外，您應該一律測量程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="d0981-151">Additionally, you should always measure the execution of your code.</span></span> <span data-ttu-id="d0981-152">例如，您可能會發現，在進行多執行緒處理時，與內容切換的負擔相較之下，CPU 繫結工作較不耗費資源。</span><span class="sxs-lookup"><span data-stu-id="d0981-152">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span> <span data-ttu-id="d0981-153">每個選項都有其取捨，您應該挑選適用於您情況的正確取捨。</span><span class="sxs-lookup"><span data-stu-id="d0981-153">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="d0981-154">更多範例</span><span class="sxs-lookup"><span data-stu-id="d0981-154">More examples</span></span>

<span data-ttu-id="d0981-155">下列範例示範可使用 C# 撰寫非同步程式碼的各種方式。</span><span class="sxs-lookup"><span data-stu-id="d0981-155">The following examples demonstrate various ways you can write async code in C#.</span></span> <span data-ttu-id="d0981-156">它們會涵蓋數個您可能會遇到的不同案例。</span><span class="sxs-lookup"><span data-stu-id="d0981-156">They cover a few different scenarios you may come across.</span></span>

### <a name="extract-data-from-a-network"></a><span data-ttu-id="d0981-157">從網路解壓縮資料</span><span class="sxs-lookup"><span data-stu-id="d0981-157">Extract data from a network</span></span>

<span data-ttu-id="d0981-158">此程式碼片段會從首頁下載 HTML <https://dotnetfoundation.org> ，並計算字串 ".net" 在 html 中出現的次數。</span><span class="sxs-lookup"><span data-stu-id="d0981-158">This snippet downloads the HTML from the homepage at <https://dotnetfoundation.org> and counts the number of times the string ".NET" occurs in the HTML.</span></span> <span data-ttu-id="d0981-159">它會使用 ASP.NET 來定義 Web API 控制器方法，這會執行這項工作並傳回數位。</span><span class="sxs-lookup"><span data-stu-id="d0981-159">It uses ASP.NET to define a Web API controller method, which performs this task and returns the number.</span></span>

> [!NOTE]
> <span data-ttu-id="d0981-160">如果您打算在生產程式碼中執行 HTML 剖析，請不要使用規則運算式。</span><span class="sxs-lookup"><span data-stu-id="d0981-160">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="d0981-161">請改用剖析程式庫。</span><span class="sxs-lookup"><span data-stu-id="d0981-161">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="d0981-162">以下是針對通用 Windows 應用程式撰寫的相同案例，而通用 Windows 應用程式會在按下按鈕時執行相同工作︰</span><span class="sxs-lookup"><span data-stu-id="d0981-162">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a><span data-ttu-id="d0981-163">等待多個工作完成</span><span class="sxs-lookup"><span data-stu-id="d0981-163">Wait for multiple tasks to complete</span></span>

<span data-ttu-id="d0981-164">您可能會發現必須同時擷取多個資料片段。</span><span class="sxs-lookup"><span data-stu-id="d0981-164">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span> <span data-ttu-id="d0981-165">此 `Task` API 包含兩種方法： <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> ，可讓您撰寫非同步程式碼，在多個背景工作上執行非封鎖等候。</span><span class="sxs-lookup"><span data-stu-id="d0981-165">The `Task` API contains two methods, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, that allow you to write asynchronous code that performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="d0981-166">這個範例示範如何捕捉一組 `userId` 的 `User` 資料。</span><span class="sxs-lookup"><span data-stu-id="d0981-166">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="d0981-167">以下是使用 LINQ 撰寫更簡潔的另一種方式：</span><span class="sxs-lookup"><span data-stu-id="d0981-167">Here's another way to write this more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="d0981-168">雖然程式碼較少，但混用 LINQ 與非同步程式碼時請務必小心。</span><span class="sxs-lookup"><span data-stu-id="d0981-168">Although it's less code, use caution when mixing LINQ with asynchronous code.</span></span> <span data-ttu-id="d0981-169">因為 LINQ 使用延後 (延遲) 執行，所以除非使用 `.ToList()` 或 `.ToArray()` 呼叫強制逐一查看產生的序列，否則不會像在 `foreach` 迴圈中一樣立即進行非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="d0981-169">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="d0981-170">重要資訊與建議</span><span class="sxs-lookup"><span data-stu-id="d0981-170">Important info and advice</span></span>

<span data-ttu-id="d0981-171">在非同步程式設計中，有一些要牢記在心的詳細資料，這可能會導致非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="d0981-171">With async programming there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="d0981-172">`async` **方法需要其主體中有** `await` **關鍵字，否則它們將永遠不會產生！**</span><span class="sxs-lookup"><span data-stu-id="d0981-172">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

  <span data-ttu-id="d0981-173">這是需要記住的重要事項。</span><span class="sxs-lookup"><span data-stu-id="d0981-173">This is important to keep in mind.</span></span> <span data-ttu-id="d0981-174">如果 `await` 不是在方法的主體中使用 `async` ，則 c # 編譯器會產生警告，但程式碼會編譯並執行，就像是一般方法一樣。</span><span class="sxs-lookup"><span data-stu-id="d0981-174">If `await` is not used in the body of an `async` method, the C# compiler generates a warning, but the code compiles and runs as if it were a normal method.</span></span> <span data-ttu-id="d0981-175">這項作業非常沒有效率，因為非同步方法的 c # 編譯器所產生的狀態機器不會完成任何作業。</span><span class="sxs-lookup"><span data-stu-id="d0981-175">This is incredibly inefficient, as the state machine generated by the C# compiler for the async method is not accomplishing anything.</span></span>

* <span data-ttu-id="d0981-176">**您應該新增 "Async" 作為您所撰寫之每個非同步方法名稱的尾碼。**</span><span class="sxs-lookup"><span data-stu-id="d0981-176">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="d0981-177">這是 .NET 中用來更輕鬆區分同步和非同步方法的慣例。</span><span class="sxs-lookup"><span data-stu-id="d0981-177">This is the convention used in .NET to more easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="d0981-178">不一定會套用您的程式碼未明確呼叫的某些方法（例如事件處理常式或 web 控制器方法）。</span><span class="sxs-lookup"><span data-stu-id="d0981-178">Certain methods that aren't explicitly called by your code (such as event handlers or web controller methods) don't necessarily apply.</span></span> <span data-ttu-id="d0981-179">因為您的程式碼並未明確呼叫它們，所以明確指出其命名並不重要。</span><span class="sxs-lookup"><span data-stu-id="d0981-179">Because they are not explicitly called by your code, being explicit about their naming isn't as important.</span></span>

* <span data-ttu-id="d0981-180">`async void` **應該只用於事件處理常式。**</span><span class="sxs-lookup"><span data-stu-id="d0981-180">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="d0981-181">因為事件沒有傳回型別 (因此無法利用 `Task` 和 `Task<T>`)，所以 `async void` 是允許非同步事件處理常式運作的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="d0981-181">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="d0981-182">`async void` 的任何其他使用都未遵循 TAP 模型，而且不容易使用，例如：</span><span class="sxs-lookup"><span data-stu-id="d0981-182">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="d0981-183">在方法中擲回的例外狀況 `async void` 無法在該方法之外捕捉。</span><span class="sxs-lookup"><span data-stu-id="d0981-183">Exceptions thrown in an `async void` method can't be caught outside of that method.</span></span>
* <span data-ttu-id="d0981-184">`async void`方法很容易測試。</span><span class="sxs-lookup"><span data-stu-id="d0981-184">`async void` methods are difficult to test.</span></span>
* <span data-ttu-id="d0981-185">`async void`如果呼叫端不希望它們是非同步，方法可能會造成不良的副作用。</span><span class="sxs-lookup"><span data-stu-id="d0981-185">`async void` methods can cause bad side effects if the caller isn't expecting them to be async.</span></span>

* <span data-ttu-id="d0981-186">**在 LINQ 運算式中使用非同步 Lambda 時，請小心處理**</span><span class="sxs-lookup"><span data-stu-id="d0981-186">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="d0981-187">LINQ 中的 Lambda 運算式會使用延後執行，這表示程式碼可能會在您不想要的時候結束執行。</span><span class="sxs-lookup"><span data-stu-id="d0981-187">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you're not expecting it to.</span></span> <span data-ttu-id="d0981-188">如果未正確撰寫，則將封鎖工作導入這個作業很容易會造成死結。</span><span class="sxs-lookup"><span data-stu-id="d0981-188">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="d0981-189">此外，這類非同步程式碼的巢狀結構也更難分析程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="d0981-189">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="d0981-190">非同步和 LINQ 功能強大，但應該盡可能小心且清楚地一起使用。</span><span class="sxs-lookup"><span data-stu-id="d0981-190">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="d0981-191">**以非封鎖方式撰寫等候工作的程式碼**</span><span class="sxs-lookup"><span data-stu-id="d0981-191">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="d0981-192">封鎖目前的執行緒做為等候完成的方法 `Task` ，可能會導致鎖死和已封鎖的內容執行緒，而且可能需要更複雜的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="d0981-192">Blocking the current thread as a means to wait for a `Task` to complete can result in deadlocks and blocked context threads, and can require more complex error-handling.</span></span> <span data-ttu-id="d0981-193">下表提供如何處理以非封鎖方式等候工作的指引：</span><span class="sxs-lookup"><span data-stu-id="d0981-193">The following table provides guidance on how to deal with waiting for tasks in a non-blocking way:</span></span>

| <span data-ttu-id="d0981-194">目的...</span><span class="sxs-lookup"><span data-stu-id="d0981-194">Use this...</span></span>          | <span data-ttu-id="d0981-195">而不是這個項目...</span><span class="sxs-lookup"><span data-stu-id="d0981-195">Instead of this...</span></span>           | <span data-ttu-id="d0981-196">當您想要這麼做時 .。。</span><span class="sxs-lookup"><span data-stu-id="d0981-196">When wishing to do this...</span></span>                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | <span data-ttu-id="d0981-197">`Task.Wait` 或 `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="d0981-197">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="d0981-198">擷取背景工作的結果</span><span class="sxs-lookup"><span data-stu-id="d0981-198">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny`               | <span data-ttu-id="d0981-199">等候任何工作完成</span><span class="sxs-lookup"><span data-stu-id="d0981-199">Waiting for any task to complete</span></span>           |
| `await Task.WhenAll` | `Task.WaitAll`               | <span data-ttu-id="d0981-200">等候所有工作完成</span><span class="sxs-lookup"><span data-stu-id="d0981-200">Waiting for all tasks to complete</span></span>          |
| `await Task.Delay`   | `Thread.Sleep`               | <span data-ttu-id="d0981-201">等候一段時間</span><span class="sxs-lookup"><span data-stu-id="d0981-201">Waiting for a period of time</span></span>               |

* <span data-ttu-id="d0981-202">**請考慮使用** `ValueTask`**可能的話**</span><span class="sxs-lookup"><span data-stu-id="d0981-202">**Consider using** `ValueTask` **where possible**</span></span>

<span data-ttu-id="d0981-203">從非同步方法傳回 `Task` 物件可能會造成在特定路徑的效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="d0981-203">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="d0981-204">`Task` 是參考型別，因此使用它表示要配置物件。</span><span class="sxs-lookup"><span data-stu-id="d0981-204">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="d0981-205">如果使用修飾詞宣告的方法傳回快取 `async` 的結果，或同步完成，則額外的配置可能會在程式碼的效能關鍵區段中變成相當長的時間成本。</span><span class="sxs-lookup"><span data-stu-id="d0981-205">In cases where a method declared with the `async` modifier returns a cached result or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="d0981-206">如果這些配置發生在緊密迴圈中，它可能會變得成本很高。</span><span class="sxs-lookup"><span data-stu-id="d0981-206">It can become costly if those allocations occur in tight loops.</span></span> <span data-ttu-id="d0981-207">如需詳細資訊，請參閱[一般化非同步](whats-new/csharp-7.md#generalized-async-return-types)傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d0981-207">For more information, see [generalized async return types](whats-new/csharp-7.md#generalized-async-return-types).</span></span>

* <span data-ttu-id="d0981-208">**請考慮使用** `ConfigureAwait(false)`</span><span class="sxs-lookup"><span data-stu-id="d0981-208">**Consider using** `ConfigureAwait(false)`</span></span>

<span data-ttu-id="d0981-209">常見的問題是：「我應該使用 <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> 方法嗎？」。</span><span class="sxs-lookup"><span data-stu-id="d0981-209">A common question is, "when should I use the <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> method?".</span></span> <span data-ttu-id="d0981-210">方法可讓 `Task` 實例設定其 awaiter。</span><span class="sxs-lookup"><span data-stu-id="d0981-210">The method allows for a `Task` instance to configure its awaiter.</span></span> <span data-ttu-id="d0981-211">這是很重要的考慮，並不正確地設定它可能會影響效能，甚至會造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="d0981-211">This is an important consideration and setting it incorrectly could potentially have performance implications and even deadlocks.</span></span> <span data-ttu-id="d0981-212">如需的詳細資訊 `ConfigureAwait` ，請參閱[ConfigureAwait 常見問題](https://devblogs.microsoft.com/dotnet/configureawait-faq)。</span><span class="sxs-lookup"><span data-stu-id="d0981-212">For more information on `ConfigureAwait`, see the [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span></span>

* <span data-ttu-id="d0981-213">**撰寫較不具狀態的程式碼**</span><span class="sxs-lookup"><span data-stu-id="d0981-213">**Write less stateful code**</span></span>

<span data-ttu-id="d0981-214">請不要依賴全域物件的狀態或特定方法的執行。</span><span class="sxs-lookup"><span data-stu-id="d0981-214">Don't depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="d0981-215">相反地，請只取決於方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="d0981-215">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="d0981-216">為什麼？</span><span class="sxs-lookup"><span data-stu-id="d0981-216">Why?</span></span>

* <span data-ttu-id="d0981-217">程式碼會比較容易理解。</span><span class="sxs-lookup"><span data-stu-id="d0981-217">Code will be easier to reason about.</span></span>
* <span data-ttu-id="d0981-218">程式碼會比較容易測試。</span><span class="sxs-lookup"><span data-stu-id="d0981-218">Code will be easier to test.</span></span>
* <span data-ttu-id="d0981-219">混合使用非同步與同步程式碼則相當簡單。</span><span class="sxs-lookup"><span data-stu-id="d0981-219">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="d0981-220">一般可以避免追蹤條件。</span><span class="sxs-lookup"><span data-stu-id="d0981-220">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="d0981-221">根據傳回值，讓非同步程式碼的協調更為簡單。</span><span class="sxs-lookup"><span data-stu-id="d0981-221">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="d0981-222">(紅利) 它可實際與相依性插入良好搭配。</span><span class="sxs-lookup"><span data-stu-id="d0981-222">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="d0981-223">建議的目標是在程式碼中達到完全或幾乎完全的 [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) (參考透明度)。</span><span class="sxs-lookup"><span data-stu-id="d0981-223">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="d0981-224">這樣做會導致極容易預測、測試和維護的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="d0981-224">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="d0981-225">其他資源</span><span class="sxs-lookup"><span data-stu-id="d0981-225">Other resources</span></span>

* <span data-ttu-id="d0981-226">[深入了解非同步](../standard/async-in-depth.md)提供工作運作方式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d0981-226">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="d0981-227">使用 async 和 await 進行非同步程式設計（c #）</span><span class="sxs-lookup"><span data-stu-id="d0981-227">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="d0981-228">Lucian Wischik 的 [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) (非同步的六個必要祕訣) 是進行非同步程式設計的不錯資源。</span><span class="sxs-lookup"><span data-stu-id="d0981-228">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
