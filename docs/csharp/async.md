---
title: 非同步程式設計
description: 深入了解 .NET Core 提供之 C# 語言層級的非同步程式設計模型。
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 971295b85e5f2763eef87bfe9109524db2630120
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865146"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="fd8fa-103">非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="fd8fa-103">Asynchronous programming</span></span>

<span data-ttu-id="fd8fa-104">如果您有任何 I/O 繫結需求 (例如，從網路要求資料，或存取資料庫)，則會想要利用非同步程式設計。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="fd8fa-105">您也可能會有 CPU 繫結程式碼，例如執行耗費資源的計算，這也是不錯的非同步程式碼撰寫案例。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="fd8fa-106">C# 具有語言層級非同步程式設計模型，可輕鬆撰寫非同步程式碼，而不需要竄改回呼或符合支援非同步的程式庫。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="fd8fa-107">它會遵循稱為[工作式非同步模式 (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) 的模式。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="fd8fa-108">非同步模型的基本概觀</span><span class="sxs-lookup"><span data-stu-id="fd8fa-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="fd8fa-109">非同步程式設計的核心是建立非同步作業模型的 `Task` 和 `Task<T>` 物件。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="fd8fa-110">它們是受 `async` 和 `await` 關鍵字所支援。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="fd8fa-111">在大部分情況下，模型都相當簡單︰</span><span class="sxs-lookup"><span data-stu-id="fd8fa-111">The model is fairly simple in most cases:</span></span> 

<span data-ttu-id="fd8fa-112">針對 I/O 繫結程式碼，您可以 `await` 作業，這項作業會在 `async` 方法內傳回 `Task` 或 `Task<T>`。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="fd8fa-113">針對 CPU 繫結程式碼，您可以 `await` 作業，這項作業是使用 `Task.Run` 方法在背景執行緒上啟動。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="fd8fa-114">`await` 關鍵字就是顯現魔力的地方。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="fd8fa-115">它會將控制交給執行 `await` 的方法呼叫端，最後讓 UI 有回應或服務有彈性。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="fd8fa-116">有其他方法可以達成上面所連結 TAP 文章中所述的 `async` 和 `await` 以外的非同步程式碼，但本文件著重在從這點開始的語言層級建構。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="fd8fa-117">I/O 繫結範例︰從 Web 服務下載資料</span><span class="sxs-lookup"><span data-stu-id="fd8fa-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="fd8fa-118">您可能需要在按下按鈕時從 Web 服務下載一些資料，但不想要封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="fd8fa-119">只要使用下列項目，即可達成這項作業：</span><span class="sxs-lookup"><span data-stu-id="fd8fa-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="fd8fa-120">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="fd8fa-120">And that’s it!</span></span> <span data-ttu-id="fd8fa-121">這個程式碼表示目的 (非同步下載一些資料)，而不陷入與工作物件的互動。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="fd8fa-122">CPU 繫結範例：執行遊戲的計算</span><span class="sxs-lookup"><span data-stu-id="fd8fa-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="fd8fa-123">假設您正在撰寫行動遊戲，而按下按鈕可能會損壞畫面上的許多敵人。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="fd8fa-124">執行損壞計算可能十分耗費資源，而且在 UI 執行緒上這麼做會讓遊戲似乎在執行計算時暫停！</span><span class="sxs-lookup"><span data-stu-id="fd8fa-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="fd8fa-125">處理這種情形的最佳方式是啟動背景執行緒，以使用 `Task.Run` 和 `await` 結果所執行的工作。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="fd8fa-126">這可讓 UI 順暢地完成工作。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="fd8fa-127">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="fd8fa-127">And that's it!</span></span>  <span data-ttu-id="fd8fa-128">此程式碼完全表示按鈕 click 事件的目的、不需要手動管理背景執行緒，並且以非封鎖方式這麼做。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="fd8fa-129">背後作業</span><span class="sxs-lookup"><span data-stu-id="fd8fa-129">What happens under the covers</span></span>

<span data-ttu-id="fd8fa-130">有許多與非同步作業有關的移動部分。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="fd8fa-131">如果您想知道 `Task` 和 `Task<T>` 的背後作業，請查看[深入了解非同步](../standard/async-in-depth.md)一文以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="fd8fa-132">在 C# 端，編譯器會將程式碼轉換為狀態電腦，而狀態電腦會追蹤下列這類事項：在達到 `await` 時產生執行，以及在完成背景工作時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="fd8fa-133">甚於理論上的需要，這是 [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises) (非同步的承諾模型) 的實作。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="fd8fa-134">要了解的重要部分</span><span class="sxs-lookup"><span data-stu-id="fd8fa-134">Key Pieces to Understand</span></span>

*   <span data-ttu-id="fd8fa-135">非同步程式碼可以用於 I/O 繫結和 CPU 繫結程式碼，但每個案例都不同。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
*   <span data-ttu-id="fd8fa-136">非同步程式碼會使用 `Task<T>` 和 `Task`，這是用來在背景中完成建立工作模型的建構。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="fd8fa-137">`async` 關鍵字會將方法轉換為非同步方法，讓您可以在其主體中使用 `await` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
*   <span data-ttu-id="fd8fa-138">套用 `await` 關鍵字時，除非等候的工作完成，否則會暫止呼叫的方法，並將控制權返回其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
*   <span data-ttu-id="fd8fa-139">`await` 只能在非同步方法內使用。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="fd8fa-140">辨識 CPU 繫結和 I/O 繫結工作</span><span class="sxs-lookup"><span data-stu-id="fd8fa-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="fd8fa-141">本手冊的前兩個範例示範如何使用 `async` 和 `await` 進行 I/O 繫結和 CPU 繫結工作。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="fd8fa-142">這是您識別所需執行的工作是 I/O 繫結還是 CPU 繫結的關鍵，因為它會大幅影響程式碼的效能，而且可能會導致誤用特定建構。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="fd8fa-143">以下是您應該在撰寫任何程式碼之前提問的兩個問題︰</span><span class="sxs-lookup"><span data-stu-id="fd8fa-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="fd8fa-144">程式碼是否要「等候」什麼項目，例如資料庫中的資料？</span><span class="sxs-lookup"><span data-stu-id="fd8fa-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="fd8fa-145">如果您的答案為「是」，則工作是 **I/O 繫結**。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="fd8fa-146">程式碼要執行極耗費資源的計算嗎？</span><span class="sxs-lookup"><span data-stu-id="fd8fa-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="fd8fa-147">如果您的答案為「是」，則工作是 **CPU 繫結**。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-147">If you answered "yes", then your work is **CPU-bound**.</span></span>
    
<span data-ttu-id="fd8fa-148">如果您的工作是「I/O 繫結」，請使用「沒有」`Task.Run` 的 `async` 和 `await`。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="fd8fa-149">您「不應該」使用 Task Parallel Library。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="fd8fa-150">[深入了解非同步](../standard/async-in-depth.md)一文中描述這個問題的原因。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="fd8fa-151">如果您的工作是「CPU 繫結」，而且您關心回應性，請使用 `async` 和 `await`，但在「含」`Task.Run` 的其他執行緒上繁衍工作。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="fd8fa-152">如果工作適用於並行和平行處理原則，您也應該考慮使用 Task Parallel Library。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-152">If the work is appropriate for concurrency and parallelism, you should also consider using the Task Parallel Library.</span></span>

<span data-ttu-id="fd8fa-153">此外，您應該一律測量程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="fd8fa-154">例如，您可能會發現，在進行多執行緒處理時，與內容切換的負擔相較之下，CPU 繫結工作較不耗費資源。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="fd8fa-155">每個選項都有其取捨，您應該挑選適用於您情況的正確取捨。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="fd8fa-156">更多範例</span><span class="sxs-lookup"><span data-stu-id="fd8fa-156">More Examples</span></span>

<span data-ttu-id="fd8fa-157">下列範例示範可使用 C# 撰寫非同步程式碼的各種方式。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="fd8fa-158">它們會涵蓋數個您可能會遇到的不同案例。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="fd8fa-159">從網路擷取資料</span><span class="sxs-lookup"><span data-stu-id="fd8fa-159">Extracting Data from a Network</span></span>

<span data-ttu-id="fd8fa-160">此程式碼片段會從首頁 ([www.dotnetfoundation.org](https://www.dotnetfoundation.org)) 下載 HTML，並計算字串 ".NET" 在 HTML 中的出現次數。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="fd8fa-161">它會使用 ASP.NET MVC 來定義執行此工作的 Web 控制器方法，並傳回數字。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="fd8fa-162">如果您打算在生產程式碼中執行 HTML 剖析，請不要使用規則運算式。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="fd8fa-163">請改用剖析程式庫。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-163">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("http://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="fd8fa-164">以下是針對通用 Windows 應用程式撰寫的相同案例，而通用 Windows 應用程式會在按下按鈕時執行相同工作︰</span><span class="sxs-lookup"><span data-stu-id="fd8fa-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("http://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="fd8fa-165">正在等候多個工作完成</span><span class="sxs-lookup"><span data-stu-id="fd8fa-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="fd8fa-166">您可能會發現必須同時擷取多個資料片段。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="fd8fa-167">`Task` API 包含兩種方法︰`Task.WhenAll` 和 `Task.WhenAny`，可讓您撰寫非同步程式碼，以對多個背景作業執行非封鎖等候。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="fd8fa-168">這個範例示範如何捕捉一組 `userId` 的 `User` 資料。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="fd8fa-169">以下是使用 LINQ 利用更簡潔的方式撰寫這個項目的另一種方式：</span><span class="sxs-lookup"><span data-stu-id="fd8fa-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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
<span data-ttu-id="fd8fa-170">雖然程式碼較少，但是混合使用 LINQ 與非同步程式碼時請小心。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="fd8fa-171">因為 LINQ 使用延後 (延遲) 執行，所以除非使用 `.ToList()` 或 `.ToArray()` 呼叫強制逐一查看產生的序列，否則不會像在 `foreach()` 迴圈中一樣立即進行非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="fd8fa-172">重要資訊和建議</span><span class="sxs-lookup"><span data-stu-id="fd8fa-172">Important Info and Advice</span></span>

<span data-ttu-id="fd8fa-173">雖然非同步程式設計相當簡單，但是需要牢記一些詳細資料，以避免非預期的行為。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

*  <span data-ttu-id="fd8fa-174">`async` **方法需要其主體中有** `await` **關鍵字，或永遠不會產生它們！**</span><span class="sxs-lookup"><span data-stu-id="fd8fa-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="fd8fa-175">這是需要記住的重要事項。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-175">This is important to keep in mind.</span></span>  <span data-ttu-id="fd8fa-176">如果 `await` 未用於 `async` 方法的主體中，C# 編譯器將會產生警告，但程式碼的編譯和執行就像一般方法一樣。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="fd8fa-177">請注意，因為 C# 編譯器針對非同步方法所產生的狀態機器不會完成任何作業，所以這也非常沒有效率。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

*   <span data-ttu-id="fd8fa-178">**您應該新增 “Async” 作為所撰寫之每個非同步方法名稱的尾碼。**</span><span class="sxs-lookup"><span data-stu-id="fd8fa-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="fd8fa-179">這是 .NET 中所使用的慣例，可更容易區分同步與非同步方法。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="fd8fa-180">請注意，不一定會套用程式碼未明確呼叫的特定方法 (例如事件處理常式或 Web 控制器方法)。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="fd8fa-181">因為您的程式碼未明確呼叫這些方法，則明確命名並不重要。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

*   <span data-ttu-id="fd8fa-182">`async void` **應該只用於事件處理常式。**</span><span class="sxs-lookup"><span data-stu-id="fd8fa-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="fd8fa-183">因為事件沒有傳回型別 (因此無法利用 `Task` 和 `Task<T>`)，所以 `async void` 是允許非同步事件處理常式運作的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="fd8fa-184">`async void` 的任何其他使用都未遵循 TAP 模型，而且不容易使用，例如：</span><span class="sxs-lookup"><span data-stu-id="fd8fa-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  *   <span data-ttu-id="fd8fa-185">`async void` 方法中所擲回的例外狀況無法在該方法外部進行攔截。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
  *   <span data-ttu-id="fd8fa-186">`async void` 方法很難進行測試。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-186">`async void` methods are very difficult to test.</span></span>
  *   <span data-ttu-id="fd8fa-187">如果呼叫端未預期 `async void` 方法非同步執行，則這些方法可能會造成不好的副作用。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

*   <span data-ttu-id="fd8fa-188">**在 LINQ 運算式中使用非同步 Lambda 時，請小心處理**</span><span class="sxs-lookup"><span data-stu-id="fd8fa-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="fd8fa-189">LINQ 中的 Lambda 運算式會使用延後執行，這表示程式碼可以在未預期它執行時結束執行。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="fd8fa-190">如果未正確撰寫，則將封鎖工作導入這個作業很容易會造成死結。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="fd8fa-191">此外，這類非同步程式碼的巢狀結構也更難分析程式碼的執行。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="fd8fa-192">非同步和 LINQ 功能強大，但應該盡可能小心且清楚地一起使用。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

*   <span data-ttu-id="fd8fa-193">**以非封鎖方式撰寫等候工作的程式碼**</span><span class="sxs-lookup"><span data-stu-id="fd8fa-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="fd8fa-194">將封鎖目前執行緒作為等候工作完成的方式可能會造成死結和封鎖的內容執行緒，而且可能需要更為複雜的錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="fd8fa-195">下表提供如何處理以非封鎖方式等候工作的指引︰</span><span class="sxs-lookup"><span data-stu-id="fd8fa-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="fd8fa-196">使用這個項目...</span><span class="sxs-lookup"><span data-stu-id="fd8fa-196">Use this...</span></span> | <span data-ttu-id="fd8fa-197">而不是這個項目...</span><span class="sxs-lookup"><span data-stu-id="fd8fa-197">Instead of this...</span></span> | <span data-ttu-id="fd8fa-198">執行時機</span><span class="sxs-lookup"><span data-stu-id="fd8fa-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="fd8fa-199">`Task.Wait` 或 `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="fd8fa-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="fd8fa-200">擷取背景工作的結果</span><span class="sxs-lookup"><span data-stu-id="fd8fa-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="fd8fa-201">等候任何工作完成</span><span class="sxs-lookup"><span data-stu-id="fd8fa-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="fd8fa-202">等候所有工作完成</span><span class="sxs-lookup"><span data-stu-id="fd8fa-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="fd8fa-203">等候一段時間</span><span class="sxs-lookup"><span data-stu-id="fd8fa-203">Waiting for a period of time</span></span> |

*   <span data-ttu-id="fd8fa-204">**撰寫較不具狀態的程式碼**</span><span class="sxs-lookup"><span data-stu-id="fd8fa-204">**Write less stateful code**</span></span>

<span data-ttu-id="fd8fa-205">請不要取決於全域物件的狀態或特定方法的執行。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="fd8fa-206">相反地，請只取決於方法的傳回值。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="fd8fa-207">為什麼？</span><span class="sxs-lookup"><span data-stu-id="fd8fa-207">Why?</span></span>

  *   <span data-ttu-id="fd8fa-208">程式碼會比較容易理解。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-208">Code will be easier to reason about.</span></span>
  *   <span data-ttu-id="fd8fa-209">程式碼會比較容易測試。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-209">Code will be easier to test.</span></span>
  *   <span data-ttu-id="fd8fa-210">混合使用非同步與同步程式碼則相當簡單。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-210">Mixing async and synchronous code is far simpler.</span></span>
  *   <span data-ttu-id="fd8fa-211">一般可以避免追蹤條件。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-211">Race conditions can typically be avoided altogether.</span></span>
  *   <span data-ttu-id="fd8fa-212">根據傳回值，讓非同步程式碼的協調更為簡單。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-212">Depending on return values makes coordinating async code simple.</span></span>
  *   <span data-ttu-id="fd8fa-213">(紅利) 它可實際與相依性插入良好搭配。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="fd8fa-214">建議的目標是在程式碼中達到完全或幾乎完全的 [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) (參考透明度)。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="fd8fa-215">這樣做會導致極容易預測、測試和維護的程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="fd8fa-216">其他資源</span><span class="sxs-lookup"><span data-stu-id="fd8fa-216">Other Resources</span></span>

* <span data-ttu-id="fd8fa-217">[深入了解非同步](../standard/async-in-depth.md)提供工作運作方式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="fd8fa-218">使用 async 和 await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="fd8fa-218">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)
* <span data-ttu-id="fd8fa-219">Lucian Wischik 的 [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) (非同步的六個必要祕訣) 是進行非同步程式設計的不錯資源。</span><span class="sxs-lookup"><span data-stu-id="fd8fa-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
