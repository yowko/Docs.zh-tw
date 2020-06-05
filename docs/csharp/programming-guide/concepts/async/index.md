---
title: C# 中的非同步程式設計
description: 使用 async、await、Task 和 Task<T> 進行非同步程式設計的 C# 語言支援概觀
ms.date: 06/04/2020
ms.openlocfilehash: fbbd08f8c0e650c366ca1d283825e629fcb952d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446423"
---
# <a name="asynchronous-programming-with-async-and-await"></a><span data-ttu-id="c52c0-103">使用 async 和 await 進行非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="c52c0-103">Asynchronous programming with async and await</span></span>

<span data-ttu-id="c52c0-104">[非同步程式設計模型（](task-asynchronous-programming-model.md)點按）工作會提供非同步程式碼的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="c52c0-104">The [Task asynchronous programming model (TAP)](task-asynchronous-programming-model.md) provides an abstraction over asynchronous code.</span></span> <span data-ttu-id="c52c0-105">您可以和往常一樣，將程式碼撰寫成一連串的陳述式。</span><span class="sxs-lookup"><span data-stu-id="c52c0-105">You write code as a sequence of statements, just like always.</span></span> <span data-ttu-id="c52c0-106">您可以將該程式碼讀成每個陳述式會先完成，再開始下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="c52c0-106">You can read that code as though each statement completes before the next begins.</span></span> <span data-ttu-id="c52c0-107">編譯器會執行一些轉換，因為部分陳述式可能會開始工作，並傳回表示進行工作的 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="c52c0-107">The compiler performs a number of transformations because some of those statements may start work and return a <xref:System.Threading.Tasks.Task> that represents the ongoing work.</span></span>

<span data-ttu-id="c52c0-108">這是此語法的目標：讓程式碼讀起來就像是一連串的陳述式，但會根據外部資源配置和工作完成時間，以比較複雜的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="c52c0-108">That's the goal of this syntax: enable code that reads like a sequence of statements, but executes in a much more complicated order based on external resource allocation and when tasks complete.</span></span> <span data-ttu-id="c52c0-109">這類似於人員為包含非同步工作之程序提供指示的方式。</span><span class="sxs-lookup"><span data-stu-id="c52c0-109">It's analogous to how people give instructions for processes that include asynchronous tasks.</span></span> <span data-ttu-id="c52c0-110">在本文中，您將使用一段指示來進行早餐，以瞭解 `async` 和 `await` 關鍵字如何讓程式碼更容易理解，包括一系列的非同步指令。</span><span class="sxs-lookup"><span data-stu-id="c52c0-110">Throughout this article, you'll use an example of instructions for making a breakfast to see how the `async` and `await` keywords make it easier to reason about code, that includes a series of asynchronous instructions.</span></span> <span data-ttu-id="c52c0-111">您撰寫了類似下列清單的指示，來說明如何準備早餐：</span><span class="sxs-lookup"><span data-stu-id="c52c0-111">You'd write the instructions something like the following list to explain how to make a breakfast:</span></span>

1. <span data-ttu-id="c52c0-112">倒杯咖啡。</span><span class="sxs-lookup"><span data-stu-id="c52c0-112">Pour a cup of coffee.</span></span>
1. <span data-ttu-id="c52c0-113">熱鍋，然後煎兩顆蛋。</span><span class="sxs-lookup"><span data-stu-id="c52c0-113">Heat up a pan, then fry two eggs.</span></span>
1. <span data-ttu-id="c52c0-114">煎三片培根。</span><span class="sxs-lookup"><span data-stu-id="c52c0-114">Fry three slices of bacon.</span></span>
1. <span data-ttu-id="c52c0-115">烤兩片吐司。</span><span class="sxs-lookup"><span data-stu-id="c52c0-115">Toast two pieces of bread.</span></span>
1. <span data-ttu-id="c52c0-116">在吐司塗上奶油和果醬。</span><span class="sxs-lookup"><span data-stu-id="c52c0-116">Add butter and jam to the toast.</span></span>
1. <span data-ttu-id="c52c0-117">倒杯柳橙汁。</span><span class="sxs-lookup"><span data-stu-id="c52c0-117">Pour a glass of orange juice.</span></span>

<span data-ttu-id="c52c0-118">如果您有烹飪經驗，您會**非同步地**執行這些指示。</span><span class="sxs-lookup"><span data-stu-id="c52c0-118">If you have experience with cooking, you'd execute those instructions **asynchronously**.</span></span> <span data-ttu-id="c52c0-119">您會從為雞蛋熱鍋開始，然後開始煎培根。</span><span class="sxs-lookup"><span data-stu-id="c52c0-119">You'd start warming the pan for eggs, then start the bacon.</span></span> <span data-ttu-id="c52c0-120">等到將麵包放入烤麵包機，再開始煎蛋。</span><span class="sxs-lookup"><span data-stu-id="c52c0-120">You'd put the bread in the toaster, then start the eggs.</span></span> <span data-ttu-id="c52c0-121">在程序的每個步驟，您會開始一個工作，然後將注意轉移到其他需要您注意的工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-121">At each step of the process, you'd start a task, then turn your attention to tasks that are ready for your attention.</span></span>

<span data-ttu-id="c52c0-122">準備早餐很適合用來示範非平行的非同步工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-122">Cooking breakfast is a good example of asynchronous work that isn't parallel.</span></span> <span data-ttu-id="c52c0-123">一個人 (或執行緒) 可處理所有這些工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-123">One person (or thread) can handle all these tasks.</span></span> <span data-ttu-id="c52c0-124">繼續以早餐為例，一個人可能會以非同步方式準備早餐，不等到第一個工作完成，就開始下一個工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-124">Continuing the breakfast analogy, one person can make breakfast asynchronously by starting the next task before the first completes.</span></span> <span data-ttu-id="c52c0-125">不論是否有旁觀者，烹飪都會進行。</span><span class="sxs-lookup"><span data-stu-id="c52c0-125">The cooking progresses whether or not someone is watching it.</span></span> <span data-ttu-id="c52c0-126">開始為雞蛋熱鍋之後，您可以開始煎培根。</span><span class="sxs-lookup"><span data-stu-id="c52c0-126">As soon as you start warming the pan for the eggs, you can begin frying the bacon.</span></span> <span data-ttu-id="c52c0-127">等到開始煎培根，您可以將麵包放入烤麵包機。</span><span class="sxs-lookup"><span data-stu-id="c52c0-127">Once the bacon starts, you can put the bread into the toaster.</span></span>

<span data-ttu-id="c52c0-128">若要進行平行演算法，您需要多個廚師 (或執行緒)。</span><span class="sxs-lookup"><span data-stu-id="c52c0-128">For a parallel algorithm, you'd need multiple cooks (or threads).</span></span> <span data-ttu-id="c52c0-129">一個人會負責煎蛋、一個人會負責煎培根，依此類推。</span><span class="sxs-lookup"><span data-stu-id="c52c0-129">One would make the eggs, one the bacon, and so on.</span></span> <span data-ttu-id="c52c0-130">每個人只會專注於一個工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-130">Each one would be focused on just that one task.</span></span> <span data-ttu-id="c52c0-131">每個廚師 (或執行緒) 禁止以同步方式等候培根準備好翻面，或吐司彈出。</span><span class="sxs-lookup"><span data-stu-id="c52c0-131">Each cook (or thread) would be blocked synchronously waiting for bacon to be ready to flip, or the toast to pop.</span></span>

<span data-ttu-id="c52c0-132">現在，考慮將這些相同指示撰寫成 C# 陳述式：</span><span class="sxs-lookup"><span data-stu-id="c52c0-132">Now, consider those same instructions written as C# statements:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-starter/Program.cs" highlight="8-27":::

:::image type="content" source="media/synchronous-breakfast.png" alt-text="同步早餐":::

<span data-ttu-id="c52c0-134">同步準備的早餐大約需要30分鐘的時間，因為總計是每個個別工作的總和。</span><span class="sxs-lookup"><span data-stu-id="c52c0-134">The synchronously prepared breakfast, took roughly 30 minutes because the total is the sum of each individual task.</span></span>

> [!NOTE]
> <span data-ttu-id="c52c0-135">`Coffee`、 `Egg` 、 `Bacon` 、 `Toast` 和 `Juice` 類別是空的。</span><span class="sxs-lookup"><span data-stu-id="c52c0-135">The `Coffee`, `Egg`, `Bacon`, `Toast`, and `Juice` classes are empty.</span></span> <span data-ttu-id="c52c0-136">它們只是用來示範的標記類別，不包含任何屬性，也不提供其他用途。</span><span class="sxs-lookup"><span data-stu-id="c52c0-136">They are simply marker classes for the purpose of demonstration, contain no properties, and serve no other purpose.</span></span>

<span data-ttu-id="c52c0-137">電腦解譯這些指示的方式與人類不同。</span><span class="sxs-lookup"><span data-stu-id="c52c0-137">Computers don't interpret those instructions the same way people do.</span></span> <span data-ttu-id="c52c0-138">電腦會封鎖每個陳述式，直到工作完成為止，再繼續下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="c52c0-138">The computer will block on each statement until the work is complete before moving on to the next statement.</span></span> <span data-ttu-id="c52c0-139">這會導致早餐無法令人滿意。</span><span class="sxs-lookup"><span data-stu-id="c52c0-139">That creates an unsatisfying breakfast.</span></span> <span data-ttu-id="c52c0-140">後續工作必須等到先前工作完成才會開始。</span><span class="sxs-lookup"><span data-stu-id="c52c0-140">The later tasks wouldn't be started until the earlier tasks had completed.</span></span> <span data-ttu-id="c52c0-141">這會花更長的時間來準備早餐，且在上菜前，有些菜可能會變涼。</span><span class="sxs-lookup"><span data-stu-id="c52c0-141">It would take much longer to create the breakfast, and some items would have gotten cold before being served.</span></span>

<span data-ttu-id="c52c0-142">如果您想要電腦以非同步方式執行上述指示，您必須撰寫非同步程式碼。</span><span class="sxs-lookup"><span data-stu-id="c52c0-142">If you want the computer to execute the above instructions asynchronously, you must write asynchronous code.</span></span>

<span data-ttu-id="c52c0-143">這些考量對您現今撰寫的程式很重要。</span><span class="sxs-lookup"><span data-stu-id="c52c0-143">These concerns are important for the programs you write today.</span></span> <span data-ttu-id="c52c0-144">當您撰寫用戶端程式時，您想要 UI 可以回應使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="c52c0-144">When you write client programs, you want the UI to be responsive to user input.</span></span> <span data-ttu-id="c52c0-145">您的應用程式不應該讓手機在從網路下載資料時呈現凍結。</span><span class="sxs-lookup"><span data-stu-id="c52c0-145">Your application shouldn't make a phone appear frozen while it's downloading data from the web.</span></span> <span data-ttu-id="c52c0-146">當您撰寫伺服器程式時，您不想要執行緒被封鎖。</span><span class="sxs-lookup"><span data-stu-id="c52c0-146">When you write server programs, you don't want threads blocked.</span></span> <span data-ttu-id="c52c0-147">這些執行緒可能會服務其他要求。</span><span class="sxs-lookup"><span data-stu-id="c52c0-147">Those threads could be serving other requests.</span></span> <span data-ttu-id="c52c0-148">在存在替代的非同步程式碼時使用同步程式碼，會導致您無法以較不耗費成本的方式擴充。</span><span class="sxs-lookup"><span data-stu-id="c52c0-148">Using synchronous code when asynchronous alternatives exist hurts your ability to scale out less expensively.</span></span> <span data-ttu-id="c52c0-149">這些封鎖的執行緒會耗費成本。</span><span class="sxs-lookup"><span data-stu-id="c52c0-149">You pay for those blocked threads.</span></span>

<span data-ttu-id="c52c0-150">現代化應用程式需要非同步程式碼才能成功。</span><span class="sxs-lookup"><span data-stu-id="c52c0-150">Successful modern applications require asynchronous code.</span></span> <span data-ttu-id="c52c0-151">由於沒有語言支援，撰寫非同步程式碼需要回呼、完成事件，或隱藏程式碼原本意圖的其他方式。</span><span class="sxs-lookup"><span data-stu-id="c52c0-151">Without language support, writing asynchronous code required callbacks, completion events, or other means that obscured the original intent of the code.</span></span> <span data-ttu-id="c52c0-152">同步程式碼的優點是容易了解。</span><span class="sxs-lookup"><span data-stu-id="c52c0-152">The advantage of the synchronous code is that it's easy to understand.</span></span> <span data-ttu-id="c52c0-153">逐步動作讓您可以輕鬆地瀏覽與了解。</span><span class="sxs-lookup"><span data-stu-id="c52c0-153">The step-by-step actions make it easy to scan and understand.</span></span> <span data-ttu-id="c52c0-154">傳統非同步模型迫使您將重點放在程式碼的非同步本質，而不是程式碼的基本動作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-154">Traditional asynchronous models forced you to focus on the asynchronous nature of the code, not on the fundamental actions of the code.</span></span>

## <a name="dont-block-await-instead"></a><span data-ttu-id="c52c0-155">不要封鎖，而是等候</span><span class="sxs-lookup"><span data-stu-id="c52c0-155">Don't block, await instead</span></span>

<span data-ttu-id="c52c0-156">上述程式碼示範不正確的做法：建構同步程式碼來執行非同步作業。</span><span class="sxs-lookup"><span data-stu-id="c52c0-156">The preceding code demonstrates a bad practice: constructing synchronous code to perform asynchronous operations.</span></span> <span data-ttu-id="c52c0-157">如內容所指，此程式碼會防止執行緒執行任何其他工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-157">As written, this code blocks the thread executing it from doing any other work.</span></span> <span data-ttu-id="c52c0-158">在任何工作進行時，它不會遭到中斷。</span><span class="sxs-lookup"><span data-stu-id="c52c0-158">It won't be interrupted while any of the tasks are in progress.</span></span> <span data-ttu-id="c52c0-159">就像是將麵包放入烤麵包機之後，直盯著烤麵包機。</span><span class="sxs-lookup"><span data-stu-id="c52c0-159">It would be as though you stared at the toaster after putting the bread in.</span></span> <span data-ttu-id="c52c0-160">在吐司彈出之前，您不會理會任何人對您說的話。</span><span class="sxs-lookup"><span data-stu-id="c52c0-160">You'd ignore anyone talking to you until the toast popped.</span></span>

<span data-ttu-id="c52c0-161">我們將從更新此程式碼開始，讓執行緒在工作執行時不會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="c52c0-161">Let's start by updating this code so that the thread doesn't block while tasks are running.</span></span> <span data-ttu-id="c52c0-162">`await` 關鍵字提供一個非封鎖方式來開始工作，然後在工作完成時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="c52c0-162">The `await` keyword provides a non-blocking way to start a task, then continue execution when that task completes.</span></span> <span data-ttu-id="c52c0-163">準備早餐程式碼的一個簡單非同步版本看起來像下列程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="c52c0-163">A simple asynchronous version of the make a breakfast code would look like the following snippet:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V2/Program.cs" id="SnippetMain":::

> [!IMPORTANT]
> <span data-ttu-id="c52c0-164">總經過時間大致上與初始 synchonous 版本相同。</span><span class="sxs-lookup"><span data-stu-id="c52c0-164">The total elapsed time is roughly the same as the initial synchonous version.</span></span> <span data-ttu-id="c52c0-165">程式碼尚未利用一些主要功能，也就是非同步程式設計。</span><span class="sxs-lookup"><span data-stu-id="c52c0-165">The code has yet to take advantage of some of the key features asynchronous programming.</span></span>

> [!TIP]
> <span data-ttu-id="c52c0-166">、和的方法主體 `FryEggsAsync` `FryBaconAsync` `ToastBreadAsync` 全都已更新為 `Task<Egg>` 分別傳回、 `Task<Bacon>` 和 `Task<Toast>` 。</span><span class="sxs-lookup"><span data-stu-id="c52c0-166">The method bodies of the `FryEggsAsync`, `FryBaconAsync`, and `ToastBreadAsync` have all been updated to return `Task<Egg>`, `Task<Bacon>`, and `Task<Toast>` respectively.</span></span> <span data-ttu-id="c52c0-167">方法會從其原始版本重新命名，以包含 "Async" 尾碼。</span><span class="sxs-lookup"><span data-stu-id="c52c0-167">The methods are renamed from their original version to include the "Async" suffix.</span></span> <span data-ttu-id="c52c0-168">其執行方式會顯示為本文稍後的[最終版本](#final-version)的一部分。</span><span class="sxs-lookup"><span data-stu-id="c52c0-168">Their implementations are shown as part of the [final version](#final-version) later in this article.</span></span>

<span data-ttu-id="c52c0-169">此程式碼不會在煎蛋或煎培根時封鎖其他工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-169">This code doesn't block while the eggs or the bacon are cooking.</span></span> <span data-ttu-id="c52c0-170">但此程式碼也不會開始任何其他工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-170">This code won't start any other tasks though.</span></span> <span data-ttu-id="c52c0-171">您仍會將吐司放入烤麵包機，並在彈出前直盯著它瞧。</span><span class="sxs-lookup"><span data-stu-id="c52c0-171">You'd still put the toast in the toaster and stare at it until it pops.</span></span> <span data-ttu-id="c52c0-172">但至少，您會回應任何需要您注意的人。</span><span class="sxs-lookup"><span data-stu-id="c52c0-172">But at least, you'd respond to anyone that wanted your attention.</span></span> <span data-ttu-id="c52c0-173">在點了多份早餐的餐廳中，廚師可能會在第一份早餐還在準備時，就開始準備另一份早餐。</span><span class="sxs-lookup"><span data-stu-id="c52c0-173">In a restaurant where multiple orders are placed, the cook could start another breakfast while the first is cooking.</span></span>

<span data-ttu-id="c52c0-174">現在，準備早餐的執行緒在等候任何已開始但尚未完成的工作時，不會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="c52c0-174">Now, the thread working on the breakfast isn't blocked while awaiting any started task that hasn't yet finished.</span></span> <span data-ttu-id="c52c0-175">對於某些應用程式而言，只需要這項變更。</span><span class="sxs-lookup"><span data-stu-id="c52c0-175">For some applications, this change is all that's needed.</span></span> <span data-ttu-id="c52c0-176">GUI 應用程式仍會只以這項變更來回應使用者。</span><span class="sxs-lookup"><span data-stu-id="c52c0-176">A GUI application still responds to the user with just this change.</span></span> <span data-ttu-id="c52c0-177">不過在此案例中，您需要不只一項變更。</span><span class="sxs-lookup"><span data-stu-id="c52c0-177">However, for this scenario, you want more.</span></span> <span data-ttu-id="c52c0-178">您不想要循序執行每個元件工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-178">You don't want each of the component tasks to be executed sequentially.</span></span> <span data-ttu-id="c52c0-179">較好的做法是開始每個元件工作，然後等候先前的工作完成。</span><span class="sxs-lookup"><span data-stu-id="c52c0-179">It's better to start each of the component tasks before awaiting the previous task's completion.</span></span>

## <a name="start-tasks-concurrently"></a><span data-ttu-id="c52c0-180">同時開始工作</span><span class="sxs-lookup"><span data-stu-id="c52c0-180">Start tasks concurrently</span></span>

<span data-ttu-id="c52c0-181">在許多情況下，您想要立即開始數個獨立工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-181">In many scenarios, you want to start several independent tasks immediately.</span></span> <span data-ttu-id="c52c0-182">然後，在每個工作完成時，您可以繼續其他準備好的工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-182">Then, as each task finishes, you can continue other work that's ready.</span></span> <span data-ttu-id="c52c0-183">以早餐為例，這會讓您更快速地完成早餐。</span><span class="sxs-lookup"><span data-stu-id="c52c0-183">In the breakfast analogy, that's how you get breakfast done more quickly.</span></span> <span data-ttu-id="c52c0-184">您也會幾乎同時完成所有工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-184">You also get everything done close to the same time.</span></span> <span data-ttu-id="c52c0-185">因此，您會有熱騰騰的早餐。</span><span class="sxs-lookup"><span data-stu-id="c52c0-185">You'll get a hot breakfast.</span></span>

<span data-ttu-id="c52c0-186"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 和相關類型是您可以用來理解進行中工作的類別。</span><span class="sxs-lookup"><span data-stu-id="c52c0-186">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> and related types are classes you can use to reason about tasks that are in progress.</span></span> <span data-ttu-id="c52c0-187">這可讓您撰寫出更類似您實際準備早餐方式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c52c0-187">That enables you to write code that more closely resembles the way you'd actually create breakfast.</span></span> <span data-ttu-id="c52c0-188">您會同時開始煎蛋、煎培根和烤吐司。</span><span class="sxs-lookup"><span data-stu-id="c52c0-188">You'd start cooking the eggs, bacon, and toast at the same time.</span></span> <span data-ttu-id="c52c0-189">由於每個工作都需要執行動作，因此您會將注意轉移到該工作、處理下一個動作，然後等候其他需要您注意的工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-189">As each requires action, you'd turn your attention to that task, take care of the next action, then await for something else that requires your attention.</span></span>

<span data-ttu-id="c52c0-190">您會開始一個工作，並保存表示該工作的 <xref:System.Threading.Tasks.Task> 物件。</span><span class="sxs-lookup"><span data-stu-id="c52c0-190">You start a task and hold on to the <xref:System.Threading.Tasks.Task> object that represents the work.</span></span> <span data-ttu-id="c52c0-191">您會 `await` 每個工作，再處理其結果。</span><span class="sxs-lookup"><span data-stu-id="c52c0-191">You'll `await` each task before working with its result.</span></span>

<span data-ttu-id="c52c0-192">我們將對早餐程式碼進行這些變更。</span><span class="sxs-lookup"><span data-stu-id="c52c0-192">Let's make these changes to the breakfast code.</span></span> <span data-ttu-id="c52c0-193">第一個步驟是為作業儲存開始時的工作，而不是等候工作：</span><span class="sxs-lookup"><span data-stu-id="c52c0-193">The first step is to store the tasks for operations when they start, rather than awaiting them:</span></span>

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");

Task<Bacon> baconTask = FryBaconAsync(3);
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Task<Toast> toastTask = ToastBreadAsync(2);
Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");

Juice oj = PourOJ();
Console.WriteLine("oj is ready");
Console.WriteLine("Breakfast is ready!");
```

<span data-ttu-id="c52c0-194">接下來，您可以將培根與雞蛋的 `await` 陳述式移至方法結尾，並在供應早餐之前：</span><span class="sxs-lookup"><span data-stu-id="c52c0-194">Next, you can move the `await` statements for the bacon and eggs to the end of the method, before serving breakfast:</span></span>

```csharp
Coffee cup = PourCoffee();
Console.WriteLine("coffee is ready");

Task<Egg> eggsTask = FryEggsAsync(2);
Task<Bacon> baconTask = FryBaconAsync(3);
Task<Toast> toastTask = ToastBreadAsync(2);

Toast toast = await toastTask;
ApplyButter(toast);
ApplyJam(toast);
Console.WriteLine("toast is ready");
Juice oj = PourOJ();
Console.WriteLine("oj is ready");

Egg eggs = await eggsTask;
Console.WriteLine("eggs are ready");
Bacon bacon = await baconTask;
Console.WriteLine("bacon is ready");

Console.WriteLine("Breakfast is ready!");
```

:::image type="content" source="media/asynchronous-breakfast.png" alt-text="非同步早餐":::

<span data-ttu-id="c52c0-196">非同步備妥的早餐大約需要20分鐘的時間，這是因為某些工作可以同時執行。</span><span class="sxs-lookup"><span data-stu-id="c52c0-196">The asynchronously prepared breakfast took roughly 20 minutes, this is because some tasks were able to run concurrently.</span></span>

<span data-ttu-id="c52c0-197">上述程式碼的效果更好。</span><span class="sxs-lookup"><span data-stu-id="c52c0-197">The preceding code works better.</span></span> <span data-ttu-id="c52c0-198">您會同時開始所有非同步工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-198">You start all the asynchronous tasks at once.</span></span> <span data-ttu-id="c52c0-199">只有需要結果時，才會等候每個工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-199">You await each task only when you need the results.</span></span> <span data-ttu-id="c52c0-200">上述程式碼可能會類似於提出不同微服務要求，然後將結果合併成單一頁面的 Web 應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="c52c0-200">The preceding code may be similar to code in a web application that makes requests of different microservices, then combines the results into a single page.</span></span> <span data-ttu-id="c52c0-201">您會立即提出所有要求，然後 `await` 所有這些工作並撰寫網頁。</span><span class="sxs-lookup"><span data-stu-id="c52c0-201">You'll make all the requests immediately, then `await` all those tasks and compose the web page.</span></span>

## <a name="composition-with-tasks"></a><span data-ttu-id="c52c0-202">工作組合</span><span class="sxs-lookup"><span data-stu-id="c52c0-202">Composition with tasks</span></span>

 <span data-ttu-id="c52c0-203">您同時準備好早餐的每道菜，除吐司以外。</span><span class="sxs-lookup"><span data-stu-id="c52c0-203">You have everything ready for breakfast at the same time except the toast.</span></span> <span data-ttu-id="c52c0-204">準備吐司是非同步作業 (烤土司) 以及同步作業 (塗上奶油和果醬) 的組合。</span><span class="sxs-lookup"><span data-stu-id="c52c0-204">Making the toast is the composition of an asynchronous operation (toasting the bread), and synchronous operations (adding the butter and the jam).</span></span> <span data-ttu-id="c52c0-205">更新此程式碼說明一個重要概念：</span><span class="sxs-lookup"><span data-stu-id="c52c0-205">Updating this code illustrates an important concept:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c52c0-206">非同步作業後面接著同步工作的組合會是非同步作業。</span><span class="sxs-lookup"><span data-stu-id="c52c0-206">The composition of an asynchronous operation followed by synchronous work is an asynchronous operation.</span></span> <span data-ttu-id="c52c0-207">換句話說，如果作業有任何部分為非同步，則整個作業是非同步。</span><span class="sxs-lookup"><span data-stu-id="c52c0-207">Stated another way, if any portion of an operation is asynchronous, the entire operation is asynchronous.</span></span>

<span data-ttu-id="c52c0-208">上述程式碼顯示您可以使用 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 物件來保存執行中的工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-208">The preceding code showed you that you can use <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> objects to hold running tasks.</span></span> <span data-ttu-id="c52c0-209">您會 `await` 每個工作，再使用其結果。</span><span class="sxs-lookup"><span data-stu-id="c52c0-209">You `await` each task before using its result.</span></span> <span data-ttu-id="c52c0-210">下一個步驟是建立表示其他工作組合的方法。</span><span class="sxs-lookup"><span data-stu-id="c52c0-210">The next step is to create methods that represent the combination of other work.</span></span> <span data-ttu-id="c52c0-211">在供應早餐之前，您想要等候表示烤土司後再塗上奶油和果醬的工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-211">Before serving breakfast, you want to await the task that represents toasting the bread before adding butter and jam.</span></span> <span data-ttu-id="c52c0-212">您可以使用下列程式碼來表示該工作：</span><span class="sxs-lookup"><span data-stu-id="c52c0-212">You can represent that work with the following code:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" id="SnippetComposeToastTask":::

<span data-ttu-id="c52c0-213">上述方法的簽章中有 `async` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="c52c0-213">The preceding method has the `async` modifier in its signature.</span></span> <span data-ttu-id="c52c0-214">這會通知編譯器，此方法包含 `await` 陳述式，其中包含非同步作業。</span><span class="sxs-lookup"><span data-stu-id="c52c0-214">That signals to the compiler that this method contains an `await` statement; it contains asynchronous operations.</span></span> <span data-ttu-id="c52c0-215">此方法表示烤土司後再塗上奶油和果醬的工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-215">This method represents the task that toasts the bread, then adds butter and jam.</span></span> <span data-ttu-id="c52c0-216">此方法會傳回 <xref:System.Threading.Tasks.Task%601>，表示這三項作業的組合。</span><span class="sxs-lookup"><span data-stu-id="c52c0-216">This method returns a <xref:System.Threading.Tasks.Task%601> that represents the composition of those three operations.</span></span> <span data-ttu-id="c52c0-217">程式碼的 Main 區塊現在會變成：</span><span class="sxs-lookup"><span data-stu-id="c52c0-217">The main block of code now becomes:</span></span>

:::code language="csharp" source="snippets/index/AsyncBreakfast-V3/Program.cs" id="SnippetMain":::

<span data-ttu-id="c52c0-218">上述變更說明使用非同步程式碼的重要技術。</span><span class="sxs-lookup"><span data-stu-id="c52c0-218">The previous change illustrated an important technique for working with asynchronous code.</span></span> <span data-ttu-id="c52c0-219">您可以透過分隔作業，將多個工作組合成傳回一個工作的新方法。</span><span class="sxs-lookup"><span data-stu-id="c52c0-219">You compose tasks by separating the operations into a new method that returns a task.</span></span> <span data-ttu-id="c52c0-220">您可以選擇何時等候該工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-220">You can choose when to await that task.</span></span> <span data-ttu-id="c52c0-221">您可以同時開始其他工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-221">You can start other tasks concurrently.</span></span>

## <a name="await-tasks-efficiently"></a><span data-ttu-id="c52c0-222">有效率地等候工作</span><span class="sxs-lookup"><span data-stu-id="c52c0-222">Await tasks efficiently</span></span>

<span data-ttu-id="c52c0-223">上述程式碼結尾的一連串 `await` 陳述式，可以透過 `Task` 類別的方法來改善。</span><span class="sxs-lookup"><span data-stu-id="c52c0-223">The series of `await` statements at the end of the preceding code can be improved by using methods of the `Task` class.</span></span> <span data-ttu-id="c52c0-224">其中一個 API 是 <xref:System.Threading.Tasks.Task.WhenAll%2A>，它會傳回其引數清單中所有工作都已完成時所完成的 <xref:System.Threading.Tasks.Task>，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="c52c0-224">One of those APIs is <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns a <xref:System.Threading.Tasks.Task> that completes when all the tasks in its argument list have completed, as shown in the following code:</span></span>

```csharp
await Task.WhenAll(eggsTask, baconTask, toastTask);
Console.WriteLine("eggs are ready");
Console.WriteLine("bacon is ready");
Console.WriteLine("toast is ready");
Console.WriteLine("Breakfast is ready!");
```

<span data-ttu-id="c52c0-225">另一個選項是使用 <xref:System.Threading.Tasks.Task.WhenAny%2A>，它會傳回其任何引數完成時所完成的 `Task<Task>`。</span><span class="sxs-lookup"><span data-stu-id="c52c0-225">Another option is to use <xref:System.Threading.Tasks.Task.WhenAny%2A>, which returns a `Task<Task>` that completes when any of its arguments completes.</span></span> <span data-ttu-id="c52c0-226">您可以等候傳回的工作，並知道它已完成。</span><span class="sxs-lookup"><span data-stu-id="c52c0-226">You can await the returned task, knowing that it has already finished.</span></span> <span data-ttu-id="c52c0-227">下列程式碼範例示範如何使用 <xref:System.Threading.Tasks.Task.WhenAny%2A> 等候第一個工作完成，再處理其結果。</span><span class="sxs-lookup"><span data-stu-id="c52c0-227">The following code shows how you could use <xref:System.Threading.Tasks.Task.WhenAny%2A> to await the first task to finish and then process its result.</span></span> <span data-ttu-id="c52c0-228">處理完成工作的結果之後，您會從傳遞至 `WhenAny` 的工作清單中移除該完成工作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-228">After processing the result from the completed task, you remove that completed task from the list of tasks passed to `WhenAny`.</span></span>

```csharp
var breakfastTasks = new List<Task> { eggsTask, baconTask, toastTask };
while (breakfastTasks.Count > 0)
{
    Task finishedTask = await Task.WhenAny(breakfastTasks);
    if (finishedTask == eggsTask)
    {
        Console.WriteLine("eggs are ready");
    }
    else if (finishedTask == baconTask)
    {
        Console.WriteLine("bacon is ready");
    }
    else if (finishedTask == toastTask)
    {
        Console.WriteLine("toast is ready");
    }
    breakfastTasks.Remove(finishedTask);
}
```

<span data-ttu-id="c52c0-229">在所有這些變更之後，最終的程式碼版本看起來像這樣：<a id="final-version"></a></span><span class="sxs-lookup"><span data-stu-id="c52c0-229">After all those changes, the final version of the code looks like this: <a id="final-version"></a></span></span>
:::code language="csharp" source="snippets/index/AsyncBreakfast-final/Program.cs" highlight="9-40":::

:::image type="content" source="media/whenany-async-breakfast.png" alt-text="任何非同步早餐時":::

<span data-ttu-id="c52c0-231">非同步準備的早餐最終版本大約需要15分鐘的時間，這是因為某些工作可以並存執行，而且程式碼可以同時監視多個工作，並且只在需要時才採取動作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-231">The final version of the asynchronously prepared breakfast took roughly 15 minutes, this is because some tasks were able to run concurrently, and the code was able to monitor multiple tasks at once and only take action when it was needed.</span></span>

<span data-ttu-id="c52c0-232">此最終程式碼為非同步。</span><span class="sxs-lookup"><span data-stu-id="c52c0-232">This final code is asynchronous.</span></span> <span data-ttu-id="c52c0-233">它會更精確地反映人員準備早餐的方式。</span><span class="sxs-lookup"><span data-stu-id="c52c0-233">It more accurately reflects how a person would cook a breakfast.</span></span> <span data-ttu-id="c52c0-234">將上述程式碼與本文中的第一個程式碼範例做比較。</span><span class="sxs-lookup"><span data-stu-id="c52c0-234">Compare the preceding code with the first code sample in this article.</span></span> <span data-ttu-id="c52c0-235">閱讀程式碼仍會清楚了解核心動作。</span><span class="sxs-lookup"><span data-stu-id="c52c0-235">The core actions are still clear from reading the code.</span></span> <span data-ttu-id="c52c0-236">閱讀此程式碼的方式，如同閱讀本文開頭準備早餐的指示。</span><span class="sxs-lookup"><span data-stu-id="c52c0-236">You can read this code the same way you'd read those instructions for making a breakfast at the beginning of this article.</span></span> <span data-ttu-id="c52c0-237">`async` 和 `await` 之語言功能為所有遵循下列書面指示的人員提供轉譯：盡可能開始多個工作且不要防止等候工作完成。</span><span class="sxs-lookup"><span data-stu-id="c52c0-237">The language features for `async` and `await` provide the translation every person makes to follow those written instructions: start tasks as you can and don't block waiting for tasks to complete.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c52c0-238">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c52c0-238">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c52c0-239">瞭解非同步程式設計模型工作</span><span class="sxs-lookup"><span data-stu-id="c52c0-239">Learn about the task asynchronous programming model</span></span>](task-asynchronous-programming-model.md)
