---
title: 撰寫大型、可回應的 .NET Framework 應用程式
ms.date: 03/30/2017
ms.assetid: 123457ac-4223-4273-bb58-3bc0e4957e9d
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 846d41c31687df98b019f103e42cf586a23d8ff1
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457549"
---
# <a name="writing-large-responsive-net-framework-apps"></a><span data-ttu-id="f6874-102">撰寫大型、可回應的 .NET Framework 應用程式</span><span class="sxs-lookup"><span data-stu-id="f6874-102">Writing Large, Responsive .NET Framework Apps</span></span>
<span data-ttu-id="f6874-103">本文針對大型 .NET Framework 應用程式或處理大量資料 (例如檔案或資料庫) 的應用程式，提供可提升其效能的提示。</span><span class="sxs-lookup"><span data-stu-id="f6874-103">This article provides tips for improving the performance of large .NET Framework apps, or apps that process a large amount of data such as files or databases.</span></span> <span data-ttu-id="f6874-104">這些提示來自於以 Managed 程式碼重寫 C# 和 Visual Basic 編譯器，本文包含數個 C# 編譯器的實際範例。</span><span class="sxs-lookup"><span data-stu-id="f6874-104">These tips come from rewriting the C# and Visual Basic compilers in managed code, and this article includes several real examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="f6874-105">使用 .NET Framework 建置應用程式的效率很高。</span><span class="sxs-lookup"><span data-stu-id="f6874-105">The .NET Framework is highly productive for building apps.</span></span>  <span data-ttu-id="f6874-106">這些強大且安全的語言和豐富的程式庫集合，可大幅提升應用程式的建置效能。</span><span class="sxs-lookup"><span data-stu-id="f6874-106">Powerful and safe languages and a rich collection of libraries make app building highly fruitful.</span></span>  <span data-ttu-id="f6874-107">然而，生產力愈高，代表所負的責任愈大。</span><span class="sxs-lookup"><span data-stu-id="f6874-107">However, with great productivity comes responsibility.</span></span>  <span data-ttu-id="f6874-108">您應該充分利用 .NET Framework 的所有功能，但視需要隨時調整程式碼的效能。</span><span class="sxs-lookup"><span data-stu-id="f6874-108">You should use all the power of the .NET Framework, but be prepared to tune your code’s performance when needed.</span></span>  
  
## <a name="why-the-new-compiler-performance-applies-to-your-app"></a><span data-ttu-id="f6874-109">新編譯器效能適用於您的應用程式的原因</span><span class="sxs-lookup"><span data-stu-id="f6874-109">Why the new compiler performance applies to your app</span></span>  
 <span data-ttu-id="f6874-110">.NET 編譯器平台 ("Roslyn") 小組以 Managed 程式碼重寫 C# 和 Visual Basic 編譯器，提供新的應用程式開發介面，以便模型化和分析程式碼、建置工具，以及提供更豐富並感知程式碼的 Visual Studio 體驗。</span><span class="sxs-lookup"><span data-stu-id="f6874-110">The .NET Compiler Platform ("Roslyn") team rewrote the C# and Visual Basic compilers in managed code to provide new APIs for modeling and analyzing code, building tools, and enabling much richer, code-aware experiences in Visual Studio.</span></span>  <span data-ttu-id="f6874-111">重寫編譯器並在新編譯器上建置 Visual Studio 體驗，顯示了實用的效能深入資訊，適用於任何大型 .NET Framework 應用程式或任何處理大量資料的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6874-111">Rewriting the compilers and building Visual Studio experiences on the new compilers revealed useful performance insights that are applicable to any large .NET Framework app or any app that processes a lot of data.</span></span>  <span data-ttu-id="f6874-112">您不需要了解編譯器，也能利用 C# 編譯器的深入資訊和範例。</span><span class="sxs-lookup"><span data-stu-id="f6874-112">You don't need to know about compilers to take advantage of the insights and examples from the C# compiler.</span></span>  
  
 <span data-ttu-id="f6874-113">Visual Studio 使用編譯器應用程式開發介面建置使用者偏好的所有 IntelliSense 功能，例如以顏色標示識別項和關鍵字、語法完成清單、錯誤波浪線、參數提示、程式碼問題和程式碼動作。</span><span class="sxs-lookup"><span data-stu-id="f6874-113">Visual Studio uses the compiler APIs to build all the IntelliSense features that users love, such as colorization of identifiers and keywords, syntax completion lists, squiggles for errors, parameter tips, code issues, and code actions.</span></span>  <span data-ttu-id="f6874-114">Visual Studio 會在開發人員輸入及變更其程式碼時提供此說明，並且 Visual Studio 必須在編譯器持續模型化開發人員編輯的程式碼時保持回應。</span><span class="sxs-lookup"><span data-stu-id="f6874-114">Visual Studio provides this help while developers are typing and changing their code, and Visual Studio must remain responsive while the compiler continually models the code developers edit.</span></span>  
  
 <span data-ttu-id="f6874-115">當您的使用者與您的應用程式互動時，他們期望應用程式會有回應。</span><span class="sxs-lookup"><span data-stu-id="f6874-115">When your end users interact with your app, they expect it to be responsive.</span></span>  <span data-ttu-id="f6874-116">因此，請不要封鎖輸入或命令處理等動作。</span><span class="sxs-lookup"><span data-stu-id="f6874-116">Typing or command handling should never be blocked.</span></span>  <span data-ttu-id="f6874-117">說明應該迅速快顯，或在使用者繼續輸入時放棄顯示。</span><span class="sxs-lookup"><span data-stu-id="f6874-117">Help should pop up quickly or give up if the user continues typing.</span></span>  <span data-ttu-id="f6874-118">您的應用程式應該避免冗長的運算使得應用程式緩慢，而導致封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="f6874-118">Your app should avoid blocking the UI thread with long computations that make the app feel sluggish.</span></span>  
  
 <span data-ttu-id="f6874-119">如需 Roslyn 編譯器的詳細資訊，請瀏覽[dotnet/roslyn](https://github.com/dotnet/roslyn) GitHub 上的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="f6874-119">For more information about Roslyn compilers, visit the [dotnet/roslyn](https://github.com/dotnet/roslyn) repo on GitHub.</span></span>
 <!-- TODO: replace with link to Roslyn conceptual docs once that's published -->
  
## <a name="just-the-facts"></a><span data-ttu-id="f6874-120">認清事實</span><span class="sxs-lookup"><span data-stu-id="f6874-120">Just the Facts</span></span>  
 <span data-ttu-id="f6874-121">調整效能和建立回應能力佳的 .NET Framework 應用程式時，請考慮下列幾點事實。</span><span class="sxs-lookup"><span data-stu-id="f6874-121">Consider these facts when tuning performance and creating responsive .NET Framework apps.</span></span>  
  
### <a name="fact-1-dont-prematurely-optimize"></a><span data-ttu-id="f6874-122">事實 1：不要太早進行最佳化</span><span class="sxs-lookup"><span data-stu-id="f6874-122">Fact 1: Don’t prematurely optimize</span></span>  
 <span data-ttu-id="f6874-123">撰寫比所需還要複雜的程式碼，會產生維護、偵錯和修改成本。</span><span class="sxs-lookup"><span data-stu-id="f6874-123">Writing code that is more complex than it needs to be incurs maintenance, debugging, and polishing costs.</span></span>  <span data-ttu-id="f6874-124">有經驗的程式設計人員直覺便知道如何解決程式碼問題，以及如何撰寫更有效率的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-124">Experienced programmers have an intuitive grasp of how to solve coding problems and write more efficient code.</span></span>  <span data-ttu-id="f6874-125">不過，他們有時會太早最佳化程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-125">However, they sometimes prematurely optimize their code.</span></span>  <span data-ttu-id="f6874-126">例如，他們可能會在簡單陣列便已足夠的情況下，使用雜湊資料表；或者使用可能會造成記憶體流失的複雜快取，而不直接重新計算值。</span><span class="sxs-lookup"><span data-stu-id="f6874-126">For example, they use a hash table when a simple array would suffice, or use complicated caching that may leak memory instead of simply recomputing values.</span></span>  <span data-ttu-id="f6874-127">即使您是有經驗的程式設計人員，仍應測試效能，並在發現問題時分析程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-127">Even if you’re an experience programmer, you should test for performance and analyze your code when you find issues.</span></span>  
  
### <a name="fact-2-if-youre-not-measuring-youre-guessing"></a><span data-ttu-id="f6874-128">事實 2：未經測量，不過是臆測</span><span class="sxs-lookup"><span data-stu-id="f6874-128">Fact 2: If you’re not measuring, you’re guessing</span></span>  
 <span data-ttu-id="f6874-129">程式碼剖析和測量資料不會說謊。</span><span class="sxs-lookup"><span data-stu-id="f6874-129">Profiles and measurements don’t lie.</span></span>  <span data-ttu-id="f6874-130">程式碼剖析顯示 CPU 是否滿載，或者磁碟 I/O 是否發生封鎖的情況。</span><span class="sxs-lookup"><span data-stu-id="f6874-130">Profiles show you whether the CPU is fully loaded or whether you’re blocked on disk I/O.</span></span>  <span data-ttu-id="f6874-131">程式碼剖析告訴您目前配置的記憶體類型和數量，以及您的 CPU 是否花很多時間在[記憶體回收](../../../docs/standard/garbage-collection/index.md) (GC)。</span><span class="sxs-lookup"><span data-stu-id="f6874-131">Profiles tell you what kind and how much memory you’re allocating and whether your CPU is spending a lot of time in [garbage collection](../../../docs/standard/garbage-collection/index.md) (GC).</span></span>  
  
 <span data-ttu-id="f6874-132">您應該為應用程式中的關鍵客戶體驗或案例設定效能目標，並撰寫測試以測量效能。</span><span class="sxs-lookup"><span data-stu-id="f6874-132">You should set performance goals for key customer experiences or scenarios in your app and write tests to measure performance.</span></span>  <span data-ttu-id="f6874-133">應用科學方法來調查失敗的測試：使用程式碼剖析來引導您、假設可能的問題，以及透過實驗或變更程式碼來測試您的假設。</span><span class="sxs-lookup"><span data-stu-id="f6874-133">Investigate failing tests by applying the scientific method: use profiles to guide you, hypothesize what the issue might be, and test your hypothesis with an experiment or code change.</span></span>  <span data-ttu-id="f6874-134">透過定期測試建立一段時間的基準效能測量資料，以便您隔離出導致效能降低的變更。</span><span class="sxs-lookup"><span data-stu-id="f6874-134">Establish baseline performance measurements over time with regular testing, so you can isolate changes that cause regressions in performance.</span></span>  <span data-ttu-id="f6874-135">當您以嚴謹的方式來處理效能工作時，便可避免浪費時間在不必要的程式碼更新。</span><span class="sxs-lookup"><span data-stu-id="f6874-135">By approaching performance work in a rigorous way, you’ll avoid wasting time with code updates you don’t need.</span></span>  
  
### <a name="fact-3-good-tools-make-all-the-difference"></a><span data-ttu-id="f6874-136">事實 3：使用良好工具的成果大不相同</span><span class="sxs-lookup"><span data-stu-id="f6874-136">Fact 3: Good tools make all the difference</span></span>  
 <span data-ttu-id="f6874-137">良好工具可讓您快速鑽研最大的效能問題 (CPU、記憶體或磁碟)，並協助您找出導致這些瓶頸的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-137">Good tools let you drill quickly into the biggest performance issues (CPU, memory, or disk) and help you locate the code that causes those bottlenecks.</span></span>  <span data-ttu-id="f6874-138">Microsoft 提供各種效能工具，例如 [Visual Studio 程式碼剖析工具](/visualstudio/profiling/beginners-guide-to-performance-profiling)、[Windows Phone 分析工具](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f)和 [PerfView](http://www.microsoft.com/download/details.aspx?id=28567)。</span><span class="sxs-lookup"><span data-stu-id="f6874-138">Microsoft ships a variety of performance tools such as [Visual Studio Profiler](/visualstudio/profiling/beginners-guide-to-performance-profiling), [Windows Phone Analysis Tool](http://msdn.microsoft.com/library/e67e3199-ea43-4d14-ab7e-f7f19266253f), and [PerfView](http://www.microsoft.com/download/details.aspx?id=28567).</span></span>  
  
 <span data-ttu-id="f6874-139">PerfView 是非常強大的免費工具，可協助您專注於深入的問題，例如磁碟 I/O、GC 事件和記憶體。</span><span class="sxs-lookup"><span data-stu-id="f6874-139">PerfView is a free and amazingly powerful tool that helps you focus on deep issues such as disk I/O, GC events, and memory.</span></span>  <span data-ttu-id="f6874-140">您可以擷取與效能相關的 [Windows 事件追蹤](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) 事件，並輕鬆檢視每種應用程式、處理序、堆疊和執行緒的資訊。</span><span class="sxs-lookup"><span data-stu-id="f6874-140">You can capture performance-related [Event Tracing for Windows](../../../docs/framework/wcf/samples/etw-tracing.md) (ETW) events and view easily per app, per process, per stack, and per thread information.</span></span>  <span data-ttu-id="f6874-141">PerfView 顯示您的應用程式配置的記憶體數量和類型，以及哪些函式或呼叫堆疊佔用了多少記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-141">PerfView shows you how much and what kind of memory your app allocates, and which functions or call stacks contribute how much to the memory allocations.</span></span> <span data-ttu-id="f6874-142">如需詳細資訊，請參閱工具隨附的豐富說明主題、示範和影片 (例如 Channel 9 上的 [PerfView Tutorial](http://channel9.msdn.com/Series/PerfView-Tutorial) (PerfView 教學課程)。</span><span class="sxs-lookup"><span data-stu-id="f6874-142">For details, see the rich help topics, demos, and videos included with the tool (such as the [PerfView tutorials](http://channel9.msdn.com/Series/PerfView-Tutorial) on Channel 9).</span></span>  
  
### <a name="fact-4-its-all-about-allocations"></a><span data-ttu-id="f6874-143">事實 4：重點在於配置</span><span class="sxs-lookup"><span data-stu-id="f6874-143">Fact 4: It’s all about allocations</span></span>  
 <span data-ttu-id="f6874-144">您可能會認為建置回應能力佳的 .NET Framework 應用程式的重點在於演算法，例如使用快速排序取代反昇排序，但實際上卻不然。</span><span class="sxs-lookup"><span data-stu-id="f6874-144">You might think that building a responsive .NET Framework app is all about algorithms, such as using quick sort instead of bubble sort, but that's not the case.</span></span>  <span data-ttu-id="f6874-145">配置記憶體才是建置回應能力佳的應用程式的最大要素，特別是當您的應用程式很龐大或處理大量資料時。</span><span class="sxs-lookup"><span data-stu-id="f6874-145">The biggest factor in building a responsive app is allocating memory, especially when your app is very large or processes large amounts of data.</span></span>  
  
 <span data-ttu-id="f6874-146">使用新編譯器應用程式開發介面建置回應能力佳的 IDE 體驗的幾乎所有工作，都與避免配置和管理快取策略相關。</span><span class="sxs-lookup"><span data-stu-id="f6874-146">Almost all the work to build responsive IDE experiences with the new compiler APIs involved avoiding allocations and managing caching strategies.</span></span>  <span data-ttu-id="f6874-147">PerfView 追蹤顯示新的 C# 和 Visual Basic 編譯器的效能很少佔用龐大的 CPU 資源。</span><span class="sxs-lookup"><span data-stu-id="f6874-147">PerfView traces show that the performance of the new C# and Visual Basic compilers is rarely CPU bound.</span></span>  <span data-ttu-id="f6874-148">當編譯器讀取數十萬或數百萬行程式碼、讀取中繼資料或發出產生的程式碼時，可能會受限於 I/O。</span><span class="sxs-lookup"><span data-stu-id="f6874-148">The compilers can be I/O bound when reading hundreds of thousands or millions of lines of code, reading metadata, or emitting generated code.</span></span>  <span data-ttu-id="f6874-149">UI 執行緒延遲幾乎全部都是由於記憶體回收所造成。</span><span class="sxs-lookup"><span data-stu-id="f6874-149">The UI thread delays are nearly all due to garbage collection.</span></span>  <span data-ttu-id="f6874-150">.NET Framework GC 為了效能而高度調整，並在應用程式的程式碼執行同時執行大部分的工作。</span><span class="sxs-lookup"><span data-stu-id="f6874-150">The .NET Framework GC is highly tuned for performance and does much of its work concurrently while app code executes.</span></span>  <span data-ttu-id="f6874-151">但是，單一配置可能會觸發耗費大量資源的[gen2](../../../docs/standard/garbage-collection/fundamentals.md) 收集，並停止所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="f6874-151">However, a single allocation can trigger an expensive [gen2](../../../docs/standard/garbage-collection/fundamentals.md) collection, stopping all threads.</span></span>  
  
## <a name="common-allocations-and-examples"></a><span data-ttu-id="f6874-152">常見配置和範例</span><span class="sxs-lookup"><span data-stu-id="f6874-152">Common allocations and examples</span></span>  
 <span data-ttu-id="f6874-153">本節中的範例運算式隱藏了看起來很小的配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-153">The example expressions in this section have hidden allocations that appear small.</span></span>  <span data-ttu-id="f6874-154">但是，如果大型應用程式執行運算式夠多次，則可能造成數百個 MB，甚至是 GB 的配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-154">However, if a large app executes the expressions enough times, they can causes hundreds of megabytes, even gigabytes, of allocations.</span></span>  <span data-ttu-id="f6874-155">例如，模擬開發人員在編輯器中輸入的一分鐘測試，會配置數 GB 記憶體，而導致效能小組專注於輸入案例。</span><span class="sxs-lookup"><span data-stu-id="f6874-155">For example, one-minute tests that simulated a developer’s typing in the editor allocated gigabytes of memory and led the performance team to focus on typing scenarios.</span></span>  
  
### <a name="boxing"></a><span data-ttu-id="f6874-156">Boxing</span><span class="sxs-lookup"><span data-stu-id="f6874-156">Boxing</span></span>  
 <span data-ttu-id="f6874-157">當通常存留在堆疊或資料結構中的實值型別包裝在物件中時，會發生 [Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="f6874-157">[Boxing](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md) occurs when value types that normally live on the stack or in data structures are wrapped in an object.</span></span>  <span data-ttu-id="f6874-158">換句話說，您可以配置保存資料的物件，再傳回物件的指標。</span><span class="sxs-lookup"><span data-stu-id="f6874-158">That is, you allocate an object to hold the data, and then return a pointer to the object.</span></span>  <span data-ttu-id="f6874-159">.NET Framework 有時由於方法的簽章或儲存位置的類型而以 Boxing 處理值。</span><span class="sxs-lookup"><span data-stu-id="f6874-159">The .NET Framework sometimes boxes values due to the signature of a method or the type of a storage location.</span></span>  <span data-ttu-id="f6874-160">在物件中包裝實值類型會導致記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-160">Wrapping a value type in an object causes memory allocation.</span></span>  <span data-ttu-id="f6874-161">許多 Boxing 作業可能導致數 MB 或 GB 的應用程式配置，這表示您的應用程式會造成更多 GC。</span><span class="sxs-lookup"><span data-stu-id="f6874-161">Many boxing operations can contribute megabytes or gigabytes of allocations to your app, which means that your app will cause more GCs.</span></span> <span data-ttu-id="f6874-162">.NET Framework 和語言編譯器會盡可能避免 Boxing，但有時還是會在您預想不到的情況下發生。</span><span class="sxs-lookup"><span data-stu-id="f6874-162">The .NET Framework and the language compilers avoid boxing when possible, but sometimes it happens when you least expect it.</span></span>  
  
 <span data-ttu-id="f6874-163">若要在 PerfView 中查看 Boxing，請開啟追蹤，然後檢視您的應用程式之處理序名稱下的 GC Heap Alloc Stacks (請記住，PerfView 會報告所有處理序)。</span><span class="sxs-lookup"><span data-stu-id="f6874-163">To see boxing in PerfView, open a trace and look at GC Heap Alloc Stacks under your app’s process name (remember, PerfView reports on all processes).</span></span>  <span data-ttu-id="f6874-164">如果您在配置下看到類似 <xref:System.Int32?displayProperty=nameWithType> 和 <xref:System.Char?displayProperty=nameWithType> 的類型，則表示您以 Boxing 處理實值類型。</span><span class="sxs-lookup"><span data-stu-id="f6874-164">If you see types like <xref:System.Int32?displayProperty=nameWithType> and <xref:System.Char?displayProperty=nameWithType> under allocations, you are boxing value types.</span></span>  <span data-ttu-id="f6874-165">選擇其中一種類型可顯示以 Boxing 處理類型所在的堆疊和函式。</span><span class="sxs-lookup"><span data-stu-id="f6874-165">Choosing one of these types will show the stacks and functions in which they are boxed.</span></span>  
  
 <span data-ttu-id="f6874-166">**範例 1：字串方法和實值型別引數**</span><span class="sxs-lookup"><span data-stu-id="f6874-166">**Example 1: string methods and value type arguments**</span></span>  
  
 <span data-ttu-id="f6874-167">此範例程式碼描述可能不必要和多餘的 Boxing：</span><span class="sxs-lookup"><span data-stu-id="f6874-167">This sample code illustrates potentially unnecessary and excessive boxing:</span></span>  
  
```csharp  
public class Logger  
{  
    public static void WriteLine(string s) { /*...*/ }  
}  
  
public class BoxingExample  
{  
    public void Log(int id, int size)  
    {  
        var s = string.Format("{0}:{1}", id, size);  
        Logger.WriteLine(s);  
    }  
}  
```  
  
 <span data-ttu-id="f6874-168">此程式碼提供記錄功能，因此應用程式可經常呼叫 `Log` 函式，可能呼叫數百萬次。</span><span class="sxs-lookup"><span data-stu-id="f6874-168">This code provides logging functionality, so an app may call the `Log` function frequently, maybe millions of times.</span></span>  <span data-ttu-id="f6874-169">問題是 `string.Format` 的呼叫會解析成 <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> 多載。</span><span class="sxs-lookup"><span data-stu-id="f6874-169">The problem is that the call to `string.Format` resolves to the <xref:System.String.Format%28System.String%2CSystem.Object%2CSystem.Object%29> overload.</span></span>  
  
 <span data-ttu-id="f6874-170">此多載需要 .NET Framework 將 `int` 值 Boxing 為物件，以傳遞至此方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6874-170">This overload requires the .NET Framework to box the `int` values into objects to pass them to this method call.</span></span>  <span data-ttu-id="f6874-171">呼叫 `id.ToString()` 和 `size.ToString()`，並將所有字串 (即物件) 傳遞至 `string.Format` 呼叫，可修正一部分問題。</span><span class="sxs-lookup"><span data-stu-id="f6874-171">A partial fix is to call `id.ToString()` and `size.ToString()` and pass all strings (which are objects) to the `string.Format` call.</span></span>  <span data-ttu-id="f6874-172">呼叫 `ToString()` 不會配置字串，但是 `string.Format` 內仍然會發生配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-172">Calling `ToString()` does allocate a string, but that allocation will happen anyway inside `string.Format`.</span></span>  
  
 <span data-ttu-id="f6874-173">您可能會認為對 `string.Format` 的這個基本呼叫只是字串串連，而將此程式碼改寫如下：</span><span class="sxs-lookup"><span data-stu-id="f6874-173">You might consider that this basic call to `string.Format` is just string concatenation, so you might write this code instead:</span></span>  
  
```csharp  
var s = id.ToString() + ':' + size.ToString();  
```  
  
 <span data-ttu-id="f6874-174">但是，該行程式碼由於符合 <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>，因此會引進 Boxing 配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-174">However, that line of code introduces a boxing allocation because it compiles to <xref:System.String.Concat%28System.Object%2CSystem.Object%2CSystem.Object%29>.</span></span>  <span data-ttu-id="f6874-175">.NET Framework 必須以 Boxing 處理叫用 `Concat` 的字元常值。</span><span class="sxs-lookup"><span data-stu-id="f6874-175">The .NET Framework must box the character literal to invoke `Concat`</span></span>  
  
 <span data-ttu-id="f6874-176">**範例 1 的修正**</span><span class="sxs-lookup"><span data-stu-id="f6874-176">**Fix for example 1**</span></span>  
  
 <span data-ttu-id="f6874-177">完整修正很簡單。</span><span class="sxs-lookup"><span data-stu-id="f6874-177">The complete fix is simple.</span></span>  <span data-ttu-id="f6874-178">只要以字串常值取代字元常值即可，由於字串已經是物件，因此不會發生任何 Boxing：</span><span class="sxs-lookup"><span data-stu-id="f6874-178">Just replace the character literal with a string literal, which incurs no boxing because strings are already objects:</span></span>  
  
```csharp  
var s = id.ToString() + ":" + size.ToString();  
```  
  
 <span data-ttu-id="f6874-179">**範例 2：列舉 Boxing**</span><span class="sxs-lookup"><span data-stu-id="f6874-179">**Example 2: enum boxing**</span></span>  
  
 <span data-ttu-id="f6874-180">此範例由於經常使用列舉類型 (特別是在字典查閱作業中)，因此會在新的 C# 和 Visual Basic 編譯器中造成大量配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-180">This example was responsible for a huge amount of allocation in the new C# and Visual Basic compilers due to frequent use of enumeration types, especially in dictionary lookup operations.</span></span>  
  
```csharp  
public enum Color  
{  
    Red, Green, Blue  
}  
  
public class BoxingExample  
{  
    private string name;  
    private Color color;  
    public override int GetHashCode()  
    {  
        return name.GetHashCode() ^ color.GetHashCode();  
    }  
}  
```  
  
 <span data-ttu-id="f6874-181">這個問題很棘手。</span><span class="sxs-lookup"><span data-stu-id="f6874-181">This problem is very subtle.</span></span>  <span data-ttu-id="f6874-182">基於實作原因，此方法會以 Boxing 處理列舉類型的基本表示，因此 PerfView 會將此報告為 <xref:System.Enum.GetHashCode> Boxing。</span><span class="sxs-lookup"><span data-stu-id="f6874-182">PerfView would report this as <xref:System.Enum.GetHashCode> boxing because the method boxes the underlying representation of the enumeration type, for implementation reasons.</span></span>  <span data-ttu-id="f6874-183">如果您在 PerfView 中進一步檢視，您會看到 <xref:System.Enum.GetHashCode> 的每個呼叫有兩個 Boxing 配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-183">If you look closely in PerfView, you may see two boxing allocations for each call to <xref:System.Enum.GetHashCode>.</span></span>   <span data-ttu-id="f6874-184">編譯器會插入其中一個配置，而 .NET Framework 會插入另一個配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-184">The compiler inserts one, and the .NET Framework inserts the other.</span></span>  
  
 <span data-ttu-id="f6874-185">**範例 2 的修正**</span><span class="sxs-lookup"><span data-stu-id="f6874-185">**Fix for example 2**</span></span>  
  
 <span data-ttu-id="f6874-186">您可以在呼叫 <xref:System.Enum.GetHashCode> 之前轉換為基本表示，輕鬆避免這兩個配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-186">You can easily avoid both allocations by casting to the underlying representation before calling <xref:System.Enum.GetHashCode>:</span></span>  
  
```csharp  
((int)color).GetHashCode()  
```  
  
 <span data-ttu-id="f6874-187">以 Boxing 處理列舉類型的另一個常見來源是 <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="f6874-187">Another common source of boxing on enumeration types is the <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="f6874-188">傳遞至 <xref:System.Enum.HasFlag%28System.Enum%29> 的引數必須為 Boxed。</span><span class="sxs-lookup"><span data-stu-id="f6874-188">The argument passed to <xref:System.Enum.HasFlag%28System.Enum%29> has to be boxed.</span></span>  <span data-ttu-id="f6874-189">在大多數情況下，比較簡單且不需要配置的作法是以位元測試取代 <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6874-189">In most cases, replacing calls to <xref:System.Enum.HasFlag%28System.Enum%29?displayProperty=nameWithType> with a bitwise test is simpler and allocation-free.</span></span>  
  
 <span data-ttu-id="f6874-190">請記住第一點效能事實 (即不要太早進行最佳化)，不要以此方式開始重寫所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-190">Keep the first performance fact in mind (that is, don’t prematurely optimize) and don’t start rewriting all your code in this way.</span></span>    <span data-ttu-id="f6874-191">留意這些 Boxing 成本，但只在對應用程式進行程式碼分析並找出作用點之後變更程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-191">Be aware of these boxing costs, but change your code only after profiling your app and finding the hot spots.</span></span>  
  
### <a name="strings"></a><span data-ttu-id="f6874-192">字串</span><span class="sxs-lookup"><span data-stu-id="f6874-192">Strings</span></span>  
 <span data-ttu-id="f6874-193">字串操作是造成配置問題的一些最主要原因，通常會在 PerfView 中顯示為前五大配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-193">String manipulations are some of the biggest culprits for allocations, and they often show up in PerfView in the top five allocations.</span></span>  <span data-ttu-id="f6874-194">程式在序列化、JSON 和 REST 應用程式開發介面中都會用到字串。</span><span class="sxs-lookup"><span data-stu-id="f6874-194">Programs use strings for serialization, JSON, and REST APIs.</span></span>  <span data-ttu-id="f6874-195">當您無法使用列舉類型時，您可以使用字串做為與系統互通的程式設計常數。</span><span class="sxs-lookup"><span data-stu-id="f6874-195">You can use strings as programmatic constants for interoperating with systems when you can’t use enumeration types.</span></span>  <span data-ttu-id="f6874-196">當您的程式碼分析顯示字串高度影響效能時，請尋找 <xref:System.String> 方法的呼叫，例如 <xref:System.String.Format%2A>、<xref:System.String.Concat%2A>、<xref:System.String.Split%2A>、<xref:System.String.Join%2A>、<xref:System.String.Substring%2A> 等。</span><span class="sxs-lookup"><span data-stu-id="f6874-196">When your profiling shows that strings are highly affecting performance, look for calls to <xref:System.String> methods such as <xref:System.String.Format%2A>, <xref:System.String.Concat%2A>, <xref:System.String.Split%2A>, <xref:System.String.Join%2A>, <xref:System.String.Substring%2A>, and so on.</span></span>  <span data-ttu-id="f6874-197">使用 <xref:System.Text.StringBuilder> 可避免需要從許多說明建立一個字串的成本，但即使是配置 <xref:System.Text.StringBuilder> 物件也可能成為需要管理的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="f6874-197">Using <xref:System.Text.StringBuilder> to avoid the cost of creating one string from many pieces helps, but even allocating the <xref:System.Text.StringBuilder> object might become a bottleneck that you need to manage.</span></span>  
  
 <span data-ttu-id="f6874-198">**範例 3：字串作業**</span><span class="sxs-lookup"><span data-stu-id="f6874-198">**Example 3: string operations**</span></span>  
  
 <span data-ttu-id="f6874-199">C# 編譯器包含下列程式碼，用以撰寫格式化之 XML 文件註解的文字：</span><span class="sxs-lookup"><span data-stu-id="f6874-199">The C# compiler had this code that writes the text of a formatted XML doc comment:</span></span>  
  
```csharp  
public void WriteFormattedDocComment(string text)  
{  
    string[] lines = text.Split(new[] { "\r\n", "\r", "\n" },  
                                StringSplitOptions.None);  
    int numLines = lines.Length;  
    bool skipSpace = true;  
    if (lines[0].TrimStart().StartsWith("///"))  
    {  
        for (int i = 0; i < numLines; i++)  
        {  
            string trimmed = lines[i].TrimStart();  
            if (trimmed.Length < 4 || !char.IsWhiteSpace(trimmed[3]))  
            {  
                skipSpace = false;  
                break;  
            }  
        }  
        int substringStart = skipSpace ? 4 : 3;  
        for (int i = 0; i < numLines; i++)  
            WriteLine(lines[i].TrimStart().Substring(substringStart));  
    }  
    else { /* ... */ }  
```  
  
 <span data-ttu-id="f6874-200">您會看到此程式碼執行許多字串操作。</span><span class="sxs-lookup"><span data-stu-id="f6874-200">You can see that this code does a lot of string manipulation.</span></span>  <span data-ttu-id="f6874-201">此程式碼使用程式庫方法將多行程式碼分割成不同的字串、修剪空格、檢查引數 `text` 是否為 XML 文件註解，以及從多行程式碼擷取子字串。</span><span class="sxs-lookup"><span data-stu-id="f6874-201">The code uses library methods to split lines into separate strings, to trim white space, to check whether the argument `text` is an XML documentation comment, and to extract substrings from lines.</span></span>  
  
 <span data-ttu-id="f6874-202">在 `WriteFormattedDocComment` 內的第一行，`text.Split` 呼叫會在每次呼叫時，配置新的三元素陣列做為引數。</span><span class="sxs-lookup"><span data-stu-id="f6874-202">On the first line inside `WriteFormattedDocComment`, the `text.Split` call allocates a new three-element array as the argument every time it’s called.</span></span>  <span data-ttu-id="f6874-203">編譯器每次都必須發出程式碼，才能配置此陣列。</span><span class="sxs-lookup"><span data-stu-id="f6874-203">The compiler has to emit code to allocate this array each time.</span></span>  <span data-ttu-id="f6874-204">這是因為編譯器不確定 <xref:System.String.Split%2A> 是否將陣列儲存在其他位置，而其他程式碼可能修改了該位置的陣列，而影響對 `WriteFormattedDocComment` 的稍後呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6874-204">That’s because the compiler doesn’t know if <xref:System.String.Split%2A> stores the array somewhere where the array might be modified by other code, which would affect later calls to `WriteFormattedDocComment`.</span></span>  <span data-ttu-id="f6874-205">呼叫 <xref:System.String.Split%2A> 也會為 `text` 中的每一行配置一個字串，並配置其他記憶體以執行操作。</span><span class="sxs-lookup"><span data-stu-id="f6874-205">The call to <xref:System.String.Split%2A> also allocates a string for every line in `text` and allocates other memory to perform the operation.</span></span>  
  
 <span data-ttu-id="f6874-206">`WriteFormattedDocComment` 對 <xref:System.String.TrimStart%2A> 方法有三個呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6874-206">`WriteFormattedDocComment` has three calls to the <xref:System.String.TrimStart%2A> method.</span></span>  <span data-ttu-id="f6874-207">其中兩個呼叫在內部迴圈中，會複製工作和配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-207">Two are in inner loops that duplicate work and allocations.</span></span>  <span data-ttu-id="f6874-208">更糟的是，除了產生字串，呼叫不含引數的 <xref:System.String.TrimStart%2A> 方法還會配置空陣列 (針對 `params` 參數)。</span><span class="sxs-lookup"><span data-stu-id="f6874-208">To make matters worse, calling the <xref:System.String.TrimStart%2A> method with no arguments allocates an empty array (for the `params` parameter) in addition to the string result.</span></span>  
  
 <span data-ttu-id="f6874-209">最後是 <xref:System.String.Substring%2A> 方法的呼叫，此呼叫通常會配置新字串。</span><span class="sxs-lookup"><span data-stu-id="f6874-209">Lastly, there is a call to the <xref:System.String.Substring%2A> method, which usually allocates a new string.</span></span>  
  
 <span data-ttu-id="f6874-210">**範例 3 的修正**</span><span class="sxs-lookup"><span data-stu-id="f6874-210">**Fix for example 3**</span></span>  
  
 <span data-ttu-id="f6874-211">與先前的範例不同，稍微修改並無法修正這些配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-211">Unlike the earlier examples, small edits cannot fix these allocations.</span></span>  <span data-ttu-id="f6874-212">您必須退一步檢視問題，以不同的方式來解決問題。</span><span class="sxs-lookup"><span data-stu-id="f6874-212">You need to step back, look at the problem, and approach it differently.</span></span>  <span data-ttu-id="f6874-213">例如，您會注意到 `WriteFormattedDocComment()` 的引數是含有方法需要之所有資訊的字串，因此程式碼會執行更多索引作業，而不是配置許多部分字串。</span><span class="sxs-lookup"><span data-stu-id="f6874-213">For example, you'll notice that the argument to `WriteFormattedDocComment()` is a string that has all the information that the method needs, so the code could do more indexing instead of allocating many partial strings.</span></span>  
  
 <span data-ttu-id="f6874-214">編譯器的效能小組可透過類似如下的程式碼來處理所有配置：</span><span class="sxs-lookup"><span data-stu-id="f6874-214">The compiler’s performance team tackled all these allocations with code like this:</span></span>  
  
```csharp  
private int IndexOfFirstNonWhiteSpaceChar(string text, int start) {  
    while (start < text.Length && char.IsWhiteSpace(text[start])) start++;  
    return start;  
}  
  
private bool TrimmedStringStartsWith(string text, int start, string prefix) {  
    start = IndexOfFirstNonWhiteSpaceChar(text, start);  
    int len = text.Length - start;  
    if (len < prefix.Length) return false;  
    for (int i = 0; i < len; i++)  
    {  
        if (prefix[i] != text[start + i]) return false;  
    }  
    return true;  
}  
  
// etc...  
```  
  
 <span data-ttu-id="f6874-215">`WriteFormattedDocComment()` 的第一個版本已配置一個陣列、數個子字串、經修剪的子字串，以及空的 `params` 陣列。</span><span class="sxs-lookup"><span data-stu-id="f6874-215">The first version of `WriteFormattedDocComment()` allocated an array, several substrings, and a trimmed substring along with an empty `params` array.</span></span>  <span data-ttu-id="f6874-216">它也會檢查 `"///"`。</span><span class="sxs-lookup"><span data-stu-id="f6874-216">It also checked for `"///"`.</span></span>  <span data-ttu-id="f6874-217">修訂過的程式碼只會使用索引，而不會進行任何配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-217">The revised code uses only indexing and allocates nothing.</span></span>  <span data-ttu-id="f6874-218">它會找出非空格的第一個字元，並接著逐字元檢查以查看字串的開頭是否為 `"///"`。</span><span class="sxs-lookup"><span data-stu-id="f6874-218">It finds the first character that is not white space, and then checks character by character to see if the string starts with `"///"`.</span></span>  <span data-ttu-id="f6874-219">新程式碼使用 `IndexOfFirstNonWhiteSpaceChar` (而不是 <xref:System.String.TrimStart%2A>) 傳回出現非空白字元的第一個索引 (在指定的起始索引之後)。</span><span class="sxs-lookup"><span data-stu-id="f6874-219">The new code uses `IndexOfFirstNonWhiteSpaceChar` instead of <xref:System.String.TrimStart%2A> to return the first index (after a specified start index) where a non-whitespace character occurs.</span></span>  <span data-ttu-id="f6874-220">此修正並不完整，不過您可以查看如何套用類似的修正以取得完整的解決方法。</span><span class="sxs-lookup"><span data-stu-id="f6874-220">The fix is not complete, but you can see how to apply similar fixes for a complete solution.</span></span>  <span data-ttu-id="f6874-221">您可以在整個程式碼中應用此方法，來移除 `WriteFormattedDocComment()` 中的所有配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-221">By applying this approach throughout the code, you can remove all allocations in `WriteFormattedDocComment()`.</span></span>  
  
 <span data-ttu-id="f6874-222">**範例 4：StringBuilder**</span><span class="sxs-lookup"><span data-stu-id="f6874-222">**Example 4: StringBuilder**</span></span>  
  
 <span data-ttu-id="f6874-223">此範例使用 <xref:System.Text.StringBuilder> 物件。</span><span class="sxs-lookup"><span data-stu-id="f6874-223">This example uses a <xref:System.Text.StringBuilder> object.</span></span>  <span data-ttu-id="f6874-224">下列函式會為泛型類型產生完整的類型名稱：</span><span class="sxs-lookup"><span data-stu-id="f6874-224">The following function generates a full type name for generic types:</span></span>  
  
```csharp  
public class Example  
{  
    // Constructs a name like "SomeType<T1, T2, T3>"  
    public string GenerateFullTypeName(string name, int arity)  
    {  
        StringBuilder sb = new StringBuilder();  
  
        sb.Append(name);  
        if (arity != 0)  
        {  
            sb.Append("<");  
            for (int i = 1; i < arity; i++)  
            {  
                sb.Append("T"); sb.Append(i.ToString()); sb.Append(", ");  
            }  
            sb.Append("T"); sb.Append(i.ToString()); sb.Append(">");  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
 <span data-ttu-id="f6874-225">重點在於建立新的 <xref:System.Text.StringBuilder> 執行個體的程式行。</span><span class="sxs-lookup"><span data-stu-id="f6874-225">The focus is on the line that creates a new <xref:System.Text.StringBuilder> instance.</span></span>  <span data-ttu-id="f6874-226">此程式碼造成 `sb.ToString()` 的配置和 <xref:System.Text.StringBuilder> 實作中的內部配置，但是如果您需要字串結果，則無法控制這些配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-226">The code causes an allocation for `sb.ToString()` and internal allocations within the <xref:System.Text.StringBuilder> implementation, but you cannot control those allocations if you want the string result.</span></span>  
  
 <span data-ttu-id="f6874-227">**範例 4 的修正**</span><span class="sxs-lookup"><span data-stu-id="f6874-227">**Fix for example 4**</span></span>  
  
 <span data-ttu-id="f6874-228">若要修正 `StringBuilder` 物件配置，請快取此物件。</span><span class="sxs-lookup"><span data-stu-id="f6874-228">To fix the `StringBuilder` object allocation, cache the  object.</span></span>  <span data-ttu-id="f6874-229">即使快取可能拋棄的單一執行個體，仍會大幅提升效能。</span><span class="sxs-lookup"><span data-stu-id="f6874-229">Even caching a single instance that might get thrown away can improve performance significantly.</span></span>  <span data-ttu-id="f6874-230">這是此函式的新實作，會省略新的第一行和最後一行以外的所有程式碼：</span><span class="sxs-lookup"><span data-stu-id="f6874-230">This is the function’s new implementation, omitting all the code except for the new first and last lines:</span></span>  
  
```csharp  
// Constructs a name like "MyType<T1, T2, T3>"  
public string GenerateFullTypeName(string name, int arity)  
{  
    StringBuilder sb = AcquireBuilder();  
    /* Use sb as before */  
    return GetStringAndReleaseBuilder(sb);  
}  
```  
  
 <span data-ttu-id="f6874-231">主要部分是新的 `AcquireBuilder()` 和 `GetStringAndReleaseBuilder()` 函式：</span><span class="sxs-lookup"><span data-stu-id="f6874-231">The key parts are the new `AcquireBuilder()` and `GetStringAndReleaseBuilder()` functions:</span></span>  
  
```csharp  
[ThreadStatic]  
private static StringBuilder cachedStringBuilder;  
  
private static StringBuilder AcquireBuilder()  
{  
    StringBuilder result = cachedStringBuilder;  
    if (result == null)  
    {  
        return new StringBuilder();  
    }  
    result.Clear();  
    cachedStringBuilder = null;  
    return result;  
}  
  
private static string GetStringAndReleaseBuilder(StringBuilder sb)  
{  
    string result = sb.ToString();  
    cachedStringBuilder = sb;  
    return result;  
}  
```  
  
 <span data-ttu-id="f6874-232">由於新編譯器使用執行緒，因此這些實作使用執行緒靜態欄位 (<xref:System.ThreadStaticAttribute> 屬性) 來快取 <xref:System.Text.StringBuilder>，並且您有可能會放棄 `ThreadStatic` 宣告。</span><span class="sxs-lookup"><span data-stu-id="f6874-232">Because the new compilers use threading, these implementations use a thread-static field (<xref:System.ThreadStaticAttribute> attribute) to cache the <xref:System.Text.StringBuilder>, and you likely can forgo the `ThreadStatic` declaration.</span></span>  <span data-ttu-id="f6874-233">執行緒靜態欄位保存執行此程式碼之每個執行緒的唯一值。</span><span class="sxs-lookup"><span data-stu-id="f6874-233">The thread-static field holds a unique value for each thread that executes this code.</span></span>  
  
 <span data-ttu-id="f6874-234">清除並將欄位或快取設定為 null 之後，`AcquireBuilder()` 會傳回快取的 <xref:System.Text.StringBuilder> 執行個體 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="f6874-234">`AcquireBuilder()` returns the cached <xref:System.Text.StringBuilder> instance if there is one, after clearing it and setting the field or cache to null.</span></span>  <span data-ttu-id="f6874-235">否則，`AcquireBuilder()` 會建立並傳回新執行個體，並將欄位或快取保持設定為 null。</span><span class="sxs-lookup"><span data-stu-id="f6874-235">Otherwise, `AcquireBuilder()` creates a new instance and returns it, leaving the field or cache set to null.</span></span>  
  
 <span data-ttu-id="f6874-236">當您完成 <xref:System.Text.StringBuilder> 時，您可以呼叫 `GetStringAndReleaseBuilder()` 以取得字串結果、儲存欄位或快取中的 <xref:System.Text.StringBuilder> 執行個體，然後傳回結果。</span><span class="sxs-lookup"><span data-stu-id="f6874-236">When you’re done with <xref:System.Text.StringBuilder> , you call `GetStringAndReleaseBuilder()` to get the string result, save the <xref:System.Text.StringBuilder> instance in the field or cache, and then return the result.</span></span>  <span data-ttu-id="f6874-237">執行作業可能會重新輸入此程式碼，並建立多個 <xref:System.Text.StringBuilder> 物件 (不過這不常發生)。</span><span class="sxs-lookup"><span data-stu-id="f6874-237">It is possible for execution to re-enter this code and to create multiple <xref:System.Text.StringBuilder> objects (although that rarely happens).</span></span>  <span data-ttu-id="f6874-238">此程式碼只會儲存最後發行的 <xref:System.Text.StringBuilder> 執行個體，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="f6874-238">The code saves only the last released <xref:System.Text.StringBuilder> instance for later use.</span></span>  <span data-ttu-id="f6874-239">此簡單的快取策略會大幅降低新編譯器中的配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-239">This simple caching strategy significantly reduced allocations in the new compilers.</span></span>  <span data-ttu-id="f6874-240">.NET Framework 和 MSBuild ("MSBuild") 的組件使用類似的技術來提升效能。</span><span class="sxs-lookup"><span data-stu-id="f6874-240">Parts of the .NET Framework and MSBuild ("MSBuild") use a similar technique to improve performance.</span></span>  
  
 <span data-ttu-id="f6874-241">此簡單的快取策略遵守良好的快取設計，因為該策略具有大小限制。</span><span class="sxs-lookup"><span data-stu-id="f6874-241">This simple caching strategy adheres to good cache design because it has a size cap.</span></span>  <span data-ttu-id="f6874-242">但是，現在的程式碼比原始程式碼更多，這表示維護成本會更高。</span><span class="sxs-lookup"><span data-stu-id="f6874-242">However, there is more code now than in the original, which means more maintenance costs.</span></span>  <span data-ttu-id="f6874-243">您應該僅在發現效能問題時才採用快取策略，而 PerfView 顯示 <xref:System.Text.StringBuilder> 配置是影響效能的主要因素。</span><span class="sxs-lookup"><span data-stu-id="f6874-243">You should adopt the caching strategy only if you’ve found a performance problem, and PerfView has shown that <xref:System.Text.StringBuilder> allocations are a significant contributor.</span></span>  
  
### <a name="linq-and-lambdas"></a><span data-ttu-id="f6874-244">LINQ 和 Lambdas</span><span class="sxs-lookup"><span data-stu-id="f6874-244">LINQ and lambdas</span></span>  
 <span data-ttu-id="f6874-245">使用 Language-Integrated Query (LINQ) 和 Lambda 運算式是使用生產力功能的絕佳範例，稍後如果程式碼對效能造成很大的影響，您可能需要重寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-245">Using Language-Integrated Query (LINQ) and lambda expressions is a great example of using productive features that you might later find you need to rewrite if the code becomes a significant impact on performance.</span></span>  
  
 <span data-ttu-id="f6874-246">**範例 5：Lambdas、List\<T> 和 IEnumerable\<T>**</span><span class="sxs-lookup"><span data-stu-id="f6874-246">**Example 5: Lambdas, List\<T>, and IEnumerable\<T>**</span></span>  
  
 <span data-ttu-id="f6874-247">這個範例會使用 [LINQ 和功能樣式程式碼](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx)來找出編譯器模型中的符號，並指定名稱字串：</span><span class="sxs-lookup"><span data-stu-id="f6874-247">This example uses [LINQ and functional style code](http://blogs.msdn.com/b/charlie/archive/2007/01/26/anders-hejlsberg-on-linq-and-functional-programming.aspx) to find a symbol in the compiler’s model, given a name string:</span></span>  
  
```csharp  
class Symbol {  
    public string Name { get; private set; }  
    /*...*/  
}  
  
class Compiler {  
    private List<Symbol> symbols;  
    public Symbol FindMatchingSymbol(string name)  
    {  
        return symbols.FirstOrDefault(s => s.Name == name);  
    }  
}  
```  
  
 <span data-ttu-id="f6874-248">新編譯器和建置在其上的 IDE 體驗會很頻繁地呼叫 `FindMatchingSymbol()`，並且此函式的一行程式碼中有多個隱藏的配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-248">The new compiler and the IDE experiences built on it call `FindMatchingSymbol()` very frequently, and there are several hidden allocations in this function’s single line of code.</span></span>  <span data-ttu-id="f6874-249">若要檢查這些配置，請先將此函式的一行程式碼分成兩行：</span><span class="sxs-lookup"><span data-stu-id="f6874-249">To examine those allocations, first split the function’s single line of code into two lines:</span></span>  
  
```csharp  
Func<Symbol, bool> predicate = s => s.Name == name;  
     return symbols.FirstOrDefault(predicate);  
```  
  
 <span data-ttu-id="f6874-250">在第一行中，[Lambda 運算式](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) `s => s.Name == name` 會[覆蓋](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx)區域變數 `name`。</span><span class="sxs-lookup"><span data-stu-id="f6874-250">In the first line, the [lambda expression](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)`s => s.Name == name`[closes over](http://blogs.msdn.com/b/ericlippert/archive/2003/09/17/53028.aspx) the local variable `name`.</span></span>  <span data-ttu-id="f6874-251">這表示除了配置 `predicate` 保存的[委派](~/docs/csharp/language-reference/keywords/delegate.md)物件之外，此程式碼還會配置靜態類別，以維持可擷取 `name` 值的環境。</span><span class="sxs-lookup"><span data-stu-id="f6874-251">This means that in addition to allocating an object for the [delegate](~/docs/csharp/language-reference/keywords/delegate.md) that `predicate` holds, the code allocates a static class to hold the environment that captures the value of `name`.</span></span>  <span data-ttu-id="f6874-252">此編譯器產生類似如下的程式碼：</span><span class="sxs-lookup"><span data-stu-id="f6874-252">The compiler generates code like the following:</span></span>  
  
```csharp  
// Compiler-generated class to hold environment state for lambda  
private class Lambda1Environment  
{  
    public string capturedName;  
    public bool Evaluate(Symbol s)  
    {  
        return s.Name == this.capturedName;  
    }  
}  
  
// Expanded Func<Symbol, bool> predicate = s => s.Name == name;  
Lambda1Environment l = new Lambda1Environment() { capturedName = name };  
var predicate = new Func<Symbol, bool>(l.Evaluate);  
```  
  
 <span data-ttu-id="f6874-253">這兩個 `new` 配置 (一個用於環境類別，一個用於委派) 現在是明確的。</span><span class="sxs-lookup"><span data-stu-id="f6874-253">The two `new` allocations (one for the environment class and one for the delegate) are explicit now.</span></span>  
  
 <span data-ttu-id="f6874-254">接著檢視 `FirstOrDefault` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6874-254">Now look at the call to `FirstOrDefault`.</span></span> <span data-ttu-id="f6874-255"><xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 類型上的這個擴充方法也會造成配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-255">This extension method on the <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> type incurs an allocation too.</span></span>  <span data-ttu-id="f6874-256">由於 `FirstOrDefault` 將 <xref:System.Collections.Generic.IEnumerable%601> 物件當做它的第一個引數，因此您可以將呼叫擴充成下列程式碼 (稍微簡化以便討論)：</span><span class="sxs-lookup"><span data-stu-id="f6874-256">Because `FirstOrDefault` takes an <xref:System.Collections.Generic.IEnumerable%601> object as its first argument, you can expand the call to the following code (simplified a bit for discussion):</span></span>  
  
```csharp  
// Expanded return symbols.FirstOrDefault(predicate) ...  
     IEnumerable<Symbol> enumerable = symbols;  
     IEnumerator<Symbol> enumerator = enumerable.GetEnumerator();  
     while(enumerator.MoveNext())  
     {  
         if (predicate(enumerator.Current))  
             return enumerator.Current;  
     }  
     return default(Symbol);  
```  
  
 <span data-ttu-id="f6874-257">`symbols` 變數具有 <xref:System.Collections.Generic.List%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="f6874-257">The `symbols` variable has type <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="f6874-258"><xref:System.Collections.Generic.List%601> 集合類型實作 <xref:System.Collections.Generic.IEnumerable%601>，並巧妙地定義 <xref:System.Collections.Generic.IEnumerator%601> 透過 <xref:System.Collections.Generic.List%601> 實作的列舉值 (`struct` 介面)。</span><span class="sxs-lookup"><span data-stu-id="f6874-258">The <xref:System.Collections.Generic.List%601> collection type implements <xref:System.Collections.Generic.IEnumerable%601> and cleverly defines an enumerator (<xref:System.Collections.Generic.IEnumerator%601> interface) that <xref:System.Collections.Generic.List%601> implements with a `struct`.</span></span>  <span data-ttu-id="f6874-259">使用結構取代類別表示您通常會避免任何堆積配置，並進而影響記憶體回收效能。</span><span class="sxs-lookup"><span data-stu-id="f6874-259">Using a structure instead of a class means that you usually avoid any heap allocations, which, in turn, can affect garbage collection performance.</span></span>  <span data-ttu-id="f6874-260">列舉值通常可以搭配語言的 `foreach` 迴圈使用，該迴圈使用列舉值傳回時在呼叫堆疊上的列舉值結構。</span><span class="sxs-lookup"><span data-stu-id="f6874-260">Enumerators are typically used with the language’s `foreach` loop, which uses the enumerator structure as it is returned on the call stack.</span></span>  <span data-ttu-id="f6874-261">累加呼叫堆疊指標以挪出空間給物件，不會對 GC 造成堆積配置所造成的相同影響。</span><span class="sxs-lookup"><span data-stu-id="f6874-261">Incrementing the call stack pointer to make room for an object does not affect GC the way a heap allocation does.</span></span>  
  
 <span data-ttu-id="f6874-262">在擴充之 `FirstOrDefault` 呼叫的情況下，程式碼需要呼叫 `GetEnumerator()` 上的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="f6874-262">In the case of the expanded `FirstOrDefault` call, the code needs to call `GetEnumerator()` on an <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  <span data-ttu-id="f6874-263">將 `symbols` 指派給 `enumerable` 類型的 `IEnumerable<Symbol>` 變數會遺失實際物件為 <xref:System.Collections.Generic.List%601> 的資訊。</span><span class="sxs-lookup"><span data-stu-id="f6874-263">Assigning `symbols` to the `enumerable` variable of type `IEnumerable<Symbol>` loses the information that the actual object is a <xref:System.Collections.Generic.List%601>.</span></span>  <span data-ttu-id="f6874-264">這表示當程式碼擷取具有 `enumerable.GetEnumerator()` 的列舉值時，.NET Framework 必須以 Boxing 處理傳回結構，以指派給 `enumerator` 變數。</span><span class="sxs-lookup"><span data-stu-id="f6874-264">This means that when the code fetches the enumerator with `enumerable.GetEnumerator()`, the .NET Framework has to box the returned structure to assign it to the `enumerator` variable.</span></span>  
  
 <span data-ttu-id="f6874-265">**範例 5 的修正**</span><span class="sxs-lookup"><span data-stu-id="f6874-265">**Fix for example 5**</span></span>  
  
 <span data-ttu-id="f6874-266">修正方式是依照下列方式重寫 `FindMatchingSymbol`，以六行程式碼來取代一行程式碼，如此一來仍然簡潔易懂，並且容易維護。</span><span class="sxs-lookup"><span data-stu-id="f6874-266">The fix is to rewrite `FindMatchingSymbol` as follows, replacing its single line of code with six lines of code that are still concise, easy to read and understand, and easy to maintain:</span></span>  
  
```csharp  
public Symbol FindMatchingSymbol(string name)  
    {  
        foreach (Symbol s in symbols)  
        {  
            if (s.Name == name)  
                return s;  
        }  
        return null;  
    }  
```  
  
 <span data-ttu-id="f6874-267">此程式碼不使用 LINQ 擴充方法、Lambdas 或列舉值，並且不會造成配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-267">This code doesn’t use LINQ extension methods, lambdas, or enumerators, and it incurs no allocations.</span></span>  <span data-ttu-id="f6874-268">由於編譯器會將 `symbols` 集合視為 <xref:System.Collections.Generic.List%601>，並且可以將列舉值 (結構) 繫結至具有正確類型的區域變數，以避免 Boxing，因此不會有配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-268">There are no allocations because the compiler can see that the `symbols` collection is a <xref:System.Collections.Generic.List%601> and can bind the resulting enumerator (a structure) to a local variable with the right type to avoid boxing.</span></span>  <span data-ttu-id="f6874-269">此函式的原始版本即為展示 C# 能力和 .NET Framework 生產力的絕佳範例。</span><span class="sxs-lookup"><span data-stu-id="f6874-269">The original version of this function was a great example of the expressive power of C# and the productivity of the .NET Framework.</span></span>  <span data-ttu-id="f6874-270">此新的和更有效率的版本會保留這些品質，但不會加入要維護的任何複雜程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-270">This new and more efficient version preserves those qualities without adding any complex code to maintain.</span></span>  
  
### <a name="async-method-caching"></a><span data-ttu-id="f6874-271">非同步方法快取</span><span class="sxs-lookup"><span data-stu-id="f6874-271">Async method caching</span></span>  
 <span data-ttu-id="f6874-272">下一個範例顯示當您嘗試在[非同步](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)方法中使用快取的結果時，所發生的常見問題。</span><span class="sxs-lookup"><span data-stu-id="f6874-272">The next example shows a common problem when you try to use cached results in an [async](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7) method.</span></span>  
  
 <span data-ttu-id="f6874-273">**範例 6：在非同步方法中快取**</span><span class="sxs-lookup"><span data-stu-id="f6874-273">**Example 6: caching in async methods**</span></span>  
  
 <span data-ttu-id="f6874-274">建置在新的 C# 和 Visual Basic 編譯器的 Visual Studio IDE 功能會經常擷取語法樹狀目錄，並且編譯器會以非同步方式來執行作業，以保持 Visual Studio 的回應能力。</span><span class="sxs-lookup"><span data-stu-id="f6874-274">The Visual Studio IDE features built on the new C# and Visual Basic compilers frequently fetch syntax trees, and the compilers use async when doing so to keep Visual Studio responsive.</span></span>  <span data-ttu-id="f6874-275">以下是您可以撰寫以取得語法樹狀目錄之程式碼的第一個版本：</span><span class="sxs-lookup"><span data-stu-id="f6874-275">Here’s the first version of the code you might write to get a syntax tree:</span></span>  
  
```csharp  
class SyntaxTree { /*...*/ }  
  
class Parser { /*...*/  
    public SyntaxTree Syntax { get; }  
    public Task ParseSourceCode() { /*...*/ }  
}  
  
class Compilation { /*...*/  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="f6874-276">您會看到呼叫 `GetSyntaxTreeAsync()` 可具現化 `Parser`、剖析程式碼，然後傳回 <xref:System.Threading.Tasks.Task> 物件 `Task<SyntaxTree>`。</span><span class="sxs-lookup"><span data-stu-id="f6874-276">You can see that calling `GetSyntaxTreeAsync()` instantiates a `Parser`, parses the code, and then returns a <xref:System.Threading.Tasks.Task> object, `Task<SyntaxTree>`.</span></span>  <span data-ttu-id="f6874-277">耗費大量資源的部分是配置 `Parser` 執行個體和剖析程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-277">The expensive part is allocating the `Parser` instance and parsing the code.</span></span>  <span data-ttu-id="f6874-278">此函式傳回 <xref:System.Threading.Tasks.Task>，因此呼叫端可等候剖析運作，然後釋放 UI 執行緒以回應使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="f6874-278">The function returns a <xref:System.Threading.Tasks.Task> so that callers can await the parsing work and free the UI thread to be responsive to user input.</span></span>  
  
 <span data-ttu-id="f6874-279">數項 Visual Studio 功能可能會嘗試取得同一個語法樹狀目錄，因此您可以撰寫下列程式碼快取剖析結果，以節省時間和配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-279">Several Visual Studio features might try to get the same syntax tree, so you might write the following code to cache the parsing result to save time and allocations.</span></span>  <span data-ttu-id="f6874-280">不過，此程式碼會造成一項配置：</span><span class="sxs-lookup"><span data-stu-id="f6874-280">However, this code incurs an allocation:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private SyntaxTree cachedResult;  
  
    public async Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        if (this.cachedResult == null)  
        {  
            var parser = new Parser(); // allocation  
            await parser.ParseSourceCode(); // expensive  
            this.cachedResult = parser.Syntax;  
        }  
        return this.cachedResult;  
    }  
}  
```  
  
 <span data-ttu-id="f6874-281">您會看到新程式碼具有內含名為 `SyntaxTree` 之 `cachedResult` 欄位的快取。</span><span class="sxs-lookup"><span data-stu-id="f6874-281">You see that the new code with caching has a `SyntaxTree` field named `cachedResult`.</span></span>  <span data-ttu-id="f6874-282">當此欄位為 null 時，`GetSyntaxTreeAsync()` 會執行工作並將結果儲存在快取中。</span><span class="sxs-lookup"><span data-stu-id="f6874-282">When this field is null, `GetSyntaxTreeAsync()` does the work and saves the result in the cache.</span></span>  <span data-ttu-id="f6874-283">`GetSyntaxTreeAsync()` 會傳回 `SyntaxTree` 物件。</span><span class="sxs-lookup"><span data-stu-id="f6874-283">`GetSyntaxTreeAsync()` returns the `SyntaxTree` object.</span></span>  <span data-ttu-id="f6874-284">問題在於當您具有 `async` 類型的 `Task<SyntaxTree>` 函式，並傳回 `SyntaxTree` 類型的值時，編譯器會發出程式碼，配置一項 Task 以保存結果 (透過使用 `Task<SyntaxTree>.FromResult()`)。</span><span class="sxs-lookup"><span data-stu-id="f6874-284">The problem is that when you have an `async` function of type `Task<SyntaxTree>`, and you return a value of type `SyntaxTree`, the compiler emits code to allocate a Task to hold the result (by using `Task<SyntaxTree>.FromResult()`).</span></span>  <span data-ttu-id="f6874-285">此 Task 會標記為已完成，並會立即提供結果。</span><span class="sxs-lookup"><span data-stu-id="f6874-285">The Task is marked as completed, and the result is immediately available.</span></span>  <span data-ttu-id="f6874-286">在新編譯器的程式碼中，已完成的 <xref:System.Threading.Tasks.Task> 物件經常出現，使得修正這些配置可大幅提升回應能力。</span><span class="sxs-lookup"><span data-stu-id="f6874-286">In the code for the new compilers, <xref:System.Threading.Tasks.Task> objects that were already completed occurred so often that fixing these allocations improved responsiveness noticeably.</span></span>  
  
 <span data-ttu-id="f6874-287">**範例 6 的修正**</span><span class="sxs-lookup"><span data-stu-id="f6874-287">**Fix for example 6**</span></span>  
  
 <span data-ttu-id="f6874-288">若要移除已完成<xref:System.Threading.Tasks.Task>配置，您可以快取具有完成結果的 Task 物件：</span><span class="sxs-lookup"><span data-stu-id="f6874-288">To remove the completed <xref:System.Threading.Tasks.Task> allocation, you can cache the Task object with the completed result:</span></span>  
  
```csharp  
class Compilation { /*...*/  
  
    private Task<SyntaxTree> cachedResult;  
  
    public Task<SyntaxTree> GetSyntaxTreeAsync()  
    {  
        return this.cachedResult ??   
               (this.cachedResult = GetSyntaxTreeUncachedAsync());  
    }  
  
    private async Task<SyntaxTree> GetSyntaxTreeUncachedAsync()  
    {  
        var parser = new Parser(); // allocation  
        await parser.ParseSourceCode(); // expensive  
        return parser.Syntax;  
    }  
}  
```  
  
 <span data-ttu-id="f6874-289">此程式碼將 `cachedResult` 的類型變更為 `Task<SyntaxTree>`，並採用 `async` Helper 函式來保存 `GetSyntaxTreeAsync()` 中的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6874-289">This code changes the type of `cachedResult` to `Task<SyntaxTree>` and employs an `async` helper function that holds the original code from `GetSyntaxTreeAsync()`.</span></span>  <span data-ttu-id="f6874-290">`GetSyntaxTreeAsync()` 現在使用 [null 聯合運算子](../../csharp/language-reference/operators/null-coalescing-operator.md)來傳回 `cachedResult` (如果不是 null)。</span><span class="sxs-lookup"><span data-stu-id="f6874-290">`GetSyntaxTreeAsync()` now uses the [null coalescing operator](../../csharp/language-reference/operators/null-coalescing-operator.md) to return `cachedResult` if it isn't null.</span></span>  <span data-ttu-id="f6874-291">如果 `cachedResult` 為 null，則 `GetSyntaxTreeAsync()` 會呼叫 `GetSyntaxTreeUncachedAsync()` 並快取結果。</span><span class="sxs-lookup"><span data-stu-id="f6874-291">If `cachedResult` is null, then `GetSyntaxTreeAsync()` calls `GetSyntaxTreeUncachedAsync()` and caches the result.</span></span>  <span data-ttu-id="f6874-292">請注意，`GetSyntaxTreeAsync()` 不會像是程式碼的一般運作方式一樣，等候對 `GetSyntaxTreeUncachedAsync()` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f6874-292">Notice that `GetSyntaxTreeAsync()` doesn’t await the call to `GetSyntaxTreeUncachedAsync()` as the code would normally.</span></span>  <span data-ttu-id="f6874-293">不使用 await 表示當 `GetSyntaxTreeUncachedAsync()` 傳回其 <xref:System.Threading.Tasks.Task> 物件時，`GetSyntaxTreeAsync()` 會立即傳回 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="f6874-293">Not using await means that when `GetSyntaxTreeUncachedAsync()` returns its <xref:System.Threading.Tasks.Task> object, `GetSyntaxTreeAsync()` immediately returns the <xref:System.Threading.Tasks.Task>.</span></span>  <span data-ttu-id="f6874-294">現在，快取的結果是 <xref:System.Threading.Tasks.Task>，因此不會有傳回快取結果的配置。</span><span class="sxs-lookup"><span data-stu-id="f6874-294">Now, the cached result is a <xref:System.Threading.Tasks.Task>, so there are no allocations to return the cached result.</span></span>  
  
### <a name="additional-considerations"></a><span data-ttu-id="f6874-295">其他考量</span><span class="sxs-lookup"><span data-stu-id="f6874-295">Additional considerations</span></span>  
 <span data-ttu-id="f6874-296">以下是有關大型應用程式或處理大量資料的應用程式可能發生之問題的一些重點。</span><span class="sxs-lookup"><span data-stu-id="f6874-296">Here are a few more points about potential problems in large apps or apps that process a lot of data.</span></span>  
  
 <span data-ttu-id="f6874-297">**字典**</span><span class="sxs-lookup"><span data-stu-id="f6874-297">**Dictionaries**</span></span>  
  
 <span data-ttu-id="f6874-298">許多程式普遍都會用到字典，雖然字典很方便且本來就很有效率，</span><span class="sxs-lookup"><span data-stu-id="f6874-298">Dictionaries are used ubiquitously in many programs, and though dictionaries are very convenient and inherently efficient.</span></span>  <span data-ttu-id="f6874-299">但經常遭到不當使用。</span><span class="sxs-lookup"><span data-stu-id="f6874-299">However, they’re often used inappropriately.</span></span>  <span data-ttu-id="f6874-300">在 Visual Studio 和新編譯器中，分析顯示許多字典含有單一項目或為空的。</span><span class="sxs-lookup"><span data-stu-id="f6874-300">In Visual Studio and the new compilers, analysis shows that many of the dictionaries contained a single element or were empty.</span></span>  <span data-ttu-id="f6874-301">空的 <xref:System.Collections.Generic.Dictionary%602> 會含有十個欄位，並在 x86 電腦上佔用 48 個位元組的堆積。</span><span class="sxs-lookup"><span data-stu-id="f6874-301">An empty <xref:System.Collections.Generic.Dictionary%602> has ten fields and occupies 48 bytes on the heap on an x86 machine.</span></span>  <span data-ttu-id="f6874-302">當您需要透過定時查閱對應或關聯資料結構時，字典會很實用。</span><span class="sxs-lookup"><span data-stu-id="f6874-302">Dictionaries are great when you need a mapping or associative data structure with constant-time lookup.</span></span>  <span data-ttu-id="f6874-303">不過，當您只有幾個項目時，使用字典會浪費許多空間。</span><span class="sxs-lookup"><span data-stu-id="f6874-303">However, when you have only a few elements, you waste a lot of space by using a dictionary.</span></span>  <span data-ttu-id="f6874-304">相反地，您可以反覆查看 `List<KeyValuePair\<K,V>>`，速度會一樣快。</span><span class="sxs-lookup"><span data-stu-id="f6874-304">Instead, for example, you could iteratively look through a `List<KeyValuePair\<K,V>>`, just as fast.</span></span>  <span data-ttu-id="f6874-305">如果使用字典只是為了下載並讀取資料 (很常見的模式)，根據您使用的項目數，搭配 N(log(N)) 查閱使用排序陣列可能幾乎會一樣快。</span><span class="sxs-lookup"><span data-stu-id="f6874-305">If you use a dictionary only to load it with data and then read from it (a very common pattern), using a sorted array with an N(log(N)) lookup might be nearly as fast, depending on the number of elements you're using.</span></span>  
  
 <span data-ttu-id="f6874-306">**類別與結構的比較**</span><span class="sxs-lookup"><span data-stu-id="f6874-306">**Classes vs. structures**</span></span>  
  
 <span data-ttu-id="f6874-307">類別和結構在調整應用程式時，一般或多或少都會耗費空間/時間。</span><span class="sxs-lookup"><span data-stu-id="f6874-307">In a way, classes and structures provide a classic space/time tradeoff for tuning your apps.</span></span>  <span data-ttu-id="f6874-308">類別在 x86 電腦上會產生 12 位元組的額外負荷，即使沒有欄位亦然，但是由於只會以一個指標來參考類別執行個體，因此傳遞時並不會耗費大量資源。</span><span class="sxs-lookup"><span data-stu-id="f6874-308">Classes incur 12 bytes of overhead on an x86 machine even if they have no fields, but they are inexpensive to pass around because it only takes a pointer to refer to a class instance.</span></span>  <span data-ttu-id="f6874-309">結構若未 Boxed，則不會造成堆積配置，但是當您將大型結構當做函式引數或傳回值傳遞時，需要 CPU 時間以自動複製結構的所有資料成員。</span><span class="sxs-lookup"><span data-stu-id="f6874-309">Structures incur no heap allocations if they aren’t boxed, but when you pass large structures as function arguments or return values, it takes CPU time to atomically copy all the data members of the structures.</span></span>  <span data-ttu-id="f6874-310">請留意對傳回結構之屬性的重複呼叫，並快取區域變數中的屬性值，以避免過多的資料複製。</span><span class="sxs-lookup"><span data-stu-id="f6874-310">Watch out for repeated calls to properties that return structures, and cache the property’s value in a local variable to avoid excessive data copying.</span></span>  
  
 <span data-ttu-id="f6874-311">**快取**</span><span class="sxs-lookup"><span data-stu-id="f6874-311">**Caches**</span></span>  
  
 <span data-ttu-id="f6874-312">常用的效能訣竅是快取結果。</span><span class="sxs-lookup"><span data-stu-id="f6874-312">A common performance trick is to cache results.</span></span>  <span data-ttu-id="f6874-313">不過，沒有大小限制或處置原則的快取可能會造成記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="f6874-313">However, a cache without a size cap or disposal policy can be a memory leak.</span></span>  <span data-ttu-id="f6874-314">處理大量資料時，如果您在快取中佔用大量記憶體，可能會導致記憶體回收，而使得快取查閱的優點無效。</span><span class="sxs-lookup"><span data-stu-id="f6874-314">When processing large amounts of data, if you hold on to a lot of memory in caches, you can cause garbage collection to override the benefits of your cached lookups.</span></span>  
  
 <span data-ttu-id="f6874-315">在本文中，我們討論了您應該如何留意可能影響應用程式回應能力的效能瓶頸徵兆，特別是針對大型系統或處理大量資料的系統。</span><span class="sxs-lookup"><span data-stu-id="f6874-315">In this article, we discussed how you should be aware of performance bottleneck symptoms that can affect your app's responsiveness, especially for large systems or systems that process a large amount of data.</span></span> <span data-ttu-id="f6874-316">常見的原因包括 Boxing、字串操作、LINQ 和 Lambda、非同步方法中的快取、快取但不使用大小限制或處置原則、不當使用字典，以及在結構間傳遞。</span><span class="sxs-lookup"><span data-stu-id="f6874-316">Common culprits include boxing, string manipulations, LINQ and lambda, caching in async methods, caching without a size limit or disposal policy, inappropriate use of dictionaries, and passing around structures.</span></span>  <span data-ttu-id="f6874-317">請記住調整應用程式的四點事實：</span><span class="sxs-lookup"><span data-stu-id="f6874-317">Keep in mind the four facts for tuning your apps:</span></span>  
  
-   <span data-ttu-id="f6874-318">不要太早進行最佳化 - 保持生產力，並在發現問題時調整應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6874-318">Don’t prematurely optimize – be productive and tune your app when you spot problems.</span></span>  
  
-   <span data-ttu-id="f6874-319">程式碼剖析不會說謊 - 未經測量，不過是臆測。</span><span class="sxs-lookup"><span data-stu-id="f6874-319">Profiles don’t lie – you’re guessing if you’re not measuring.</span></span>  
  
-   <span data-ttu-id="f6874-320">使用良好工具的成果大不相同 - 請下載並試用 PerfView。</span><span class="sxs-lookup"><span data-stu-id="f6874-320">Good tools make all the difference – download PerfView and try it out.</span></span>  
  
-   <span data-ttu-id="f6874-321">重點在於配置 - 這是編譯器平台小組花費最多時間提升新編譯器效能的地方。</span><span class="sxs-lookup"><span data-stu-id="f6874-321">It's all about allocations – that is where the compiler platform team spent most of their time improving the performance of the new compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6874-322">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6874-322">See Also</span></span>  
 [<span data-ttu-id="f6874-323">本主題的簡報的視訊</span><span class="sxs-lookup"><span data-stu-id="f6874-323">Video of presentation of this topic</span></span>](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2013/DEV-B333)  
 [<span data-ttu-id="f6874-324">效能分析的初級開發人員指南</span><span class="sxs-lookup"><span data-stu-id="f6874-324">Beginners Guide to Performance Profiling</span></span>](/visualstudio/profiling/beginners-guide-to-performance-profiling)  
 [<span data-ttu-id="f6874-325">效能</span><span class="sxs-lookup"><span data-stu-id="f6874-325">Performance</span></span>](../../../docs/framework/performance/index.md)  
 [<span data-ttu-id="f6874-326">.NET 效能秘訣</span><span class="sxs-lookup"><span data-stu-id="f6874-326">.NET Performance Tips</span></span>](http://msdn.microsoft.com/library/ms973839.aspx)  
 [<span data-ttu-id="f6874-327">Windows Phone 效能分析工具</span><span class="sxs-lookup"><span data-stu-id="f6874-327">Windows Phone Performance Analysis Tool</span></span>](http://msdn.microsoft.com/magazine/hh781024.aspx)  
 [<span data-ttu-id="f6874-328">找出應用程式與 Visual Studio 分析工具的瓶頸</span><span class="sxs-lookup"><span data-stu-id="f6874-328">Find Application Bottlenecks with Visual Studio Profiler</span></span>](http://msdn.microsoft.com/magazine/cc337887.aspx)  
 [<span data-ttu-id="f6874-329">Channel 9 PerfView 教學課程</span><span class="sxs-lookup"><span data-stu-id="f6874-329">Channel 9 PerfView tutorials</span></span>](http://channel9.msdn.com/Series/PerfView-Tutorial)  
 [<span data-ttu-id="f6874-330">高層級的效能提示</span><span class="sxs-lookup"><span data-stu-id="f6874-330">High-level Performance Tips</span></span>](http://curah.microsoft.com/4604/improving-your-net-apps-startup-performance)  
 [<span data-ttu-id="f6874-331">dotnet/roslyn GitHub 上的儲存機制</span><span class="sxs-lookup"><span data-stu-id="f6874-331">dotnet/roslyn repo on GitHub</span></span>](https://github.com/dotnet/roslyn)
