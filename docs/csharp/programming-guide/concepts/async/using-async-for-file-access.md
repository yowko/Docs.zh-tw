---
title: '非同步檔案存取 (c # ) '
description: '瞭解如何在 c # 中使用 async 功能來存取檔案。 您可以呼叫非同步方法，而不需要使用回呼或跨方法分割程式碼。'
ms.date: 08/19/2020
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: 9a8db6004e8fff2cb39f0c350b403b56ea619e54
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812038"
---
# <a name="asynchronous-file-access-c"></a><span data-ttu-id="1babb-104">非同步檔案存取 (c # ) </span><span class="sxs-lookup"><span data-stu-id="1babb-104">Asynchronous file access (C#)</span></span>

<span data-ttu-id="1babb-105">您可以使用非同步功能來存取檔案。</span><span class="sxs-lookup"><span data-stu-id="1babb-105">You can use the async feature to access files.</span></span> <span data-ttu-id="1babb-106">使用非同步功能，您就可以呼叫非同步方法，而不需要使用回呼或將您的程式碼分散到多種方法或 Lambda 運算式上。</span><span class="sxs-lookup"><span data-stu-id="1babb-106">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="1babb-107">若要讓同步程式碼變成非同步，只要呼叫非同步方法 (而不是同步方法)，然後將幾個關鍵字新增至程式碼即可。</span><span class="sxs-lookup"><span data-stu-id="1babb-107">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>

<span data-ttu-id="1babb-108">您可能會基於下列原因將非同步功能新增至檔案存取呼叫：</span><span class="sxs-lookup"><span data-stu-id="1babb-108">You might consider the following reasons for adding asynchrony to file access calls:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1babb-109">非同步功能可讓 UI 應用程式回應速度更快，因為啟動作業的 UI 執行緒可以執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="1babb-109">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="1babb-110">如果 UI 執行緒必須執行相當耗時的程式碼 (例如超過 50 毫秒)，UI 可能會凍結到 I/O 完成，之後 UI 執行緒就可以再次處理鍵盤和滑鼠輸入以及其他事件。</span><span class="sxs-lookup"><span data-stu-id="1babb-110">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>
> - <span data-ttu-id="1babb-111">非同步功能藉由降低對執行緒的需求，來改善 ASP.NET 及其他伺服器架構應用程式的延展性。</span><span class="sxs-lookup"><span data-stu-id="1babb-111">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="1babb-112">如果應用程式針對每個回應使用專用執行緒，並同時處理一千個要求，則需要一千個執行緒。</span><span class="sxs-lookup"><span data-stu-id="1babb-112">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="1babb-113">非同步作業在等待期間，通常不需要使用執行緒。</span><span class="sxs-lookup"><span data-stu-id="1babb-113">Asynchronous operations often don't need to use a thread during the wait.</span></span> <span data-ttu-id="1babb-114">它們可能會在結束時短暫使用現有的 I/O 完成執行緒。</span><span class="sxs-lookup"><span data-stu-id="1babb-114">They use the existing I/O completion thread briefly at the end.</span></span>
> - <span data-ttu-id="1babb-115">檔案存取作業的延遲在目前情況下可能很低，但未來可能會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="1babb-115">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="1babb-116">例如，檔案可能會移至世界各地的伺服器。</span><span class="sxs-lookup"><span data-stu-id="1babb-116">For example, a file may be moved to a server that's across the world.</span></span>
> - <span data-ttu-id="1babb-117">使用非同步功能所增加的額外負荷很小。</span><span class="sxs-lookup"><span data-stu-id="1babb-117">The added overhead of using the Async feature is small.</span></span>
> - <span data-ttu-id="1babb-118">您可以輕鬆地同時執行多個非同步工作。</span><span class="sxs-lookup"><span data-stu-id="1babb-118">Asynchronous tasks can easily be run in parallel.</span></span>

## <a name="use-appropriate-classes"></a><span data-ttu-id="1babb-119">使用適當的類別</span><span class="sxs-lookup"><span data-stu-id="1babb-119">Use appropriate classes</span></span>

<span data-ttu-id="1babb-120">本主題中的簡單範例會示範 <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> 和 <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="1babb-120">The simple examples in this topic demonstrate <xref:System.IO.File.WriteAllTextAsync%2A?displayProperty=nameWithType> and <xref:System.IO.File.ReadAllTextAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1babb-121">若要對檔案 i/o 作業進行有限的控制，請使用 <xref:System.IO.FileStream> 類別，此類別的選項會導致作業系統層級發生非同步 i/o。</span><span class="sxs-lookup"><span data-stu-id="1babb-121">For finite control over the file I/O operations, use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="1babb-122">藉由使用這個選項，您可以避免在許多情況下封鎖執行緒集區執行緒。</span><span class="sxs-lookup"><span data-stu-id="1babb-122">By using this option, you can avoid blocking a thread pool thread in many cases.</span></span> <span data-ttu-id="1babb-123">若要啟用此選項，請在建構函式呼叫中指定 `useAsync=true` 或 `options=FileOptions.Asynchronous` 引數。</span><span class="sxs-lookup"><span data-stu-id="1babb-123">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>

<span data-ttu-id="1babb-124"><xref:System.IO.StreamReader> <xref:System.IO.StreamWriter> 如果您透過指定檔案路徑來直接開啟此選項，就不能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="1babb-124">You can't use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="1babb-125">不過，如果您提供它們已開啟 <xref:System.IO.FileStream> 類別的 <xref:System.IO.Stream>，則可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="1babb-125">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="1babb-126">即使執行緒集區執行緒遭到封鎖，非同步呼叫的速度也會更快，因為 UI 執行緒在等候期間不會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="1babb-126">Asynchronous calls are faster in UI apps even if a thread pool thread is blocked, because the UI thread isn't blocked during the wait.</span></span>

## <a name="write-text"></a><span data-ttu-id="1babb-127">寫入文字</span><span class="sxs-lookup"><span data-stu-id="1babb-127">Write text</span></span>

<span data-ttu-id="1babb-128">下列範例會將文字寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="1babb-128">The following examples write text to a file.</span></span> <span data-ttu-id="1babb-129">在每個 await 陳述式中，此方法會立即結束。</span><span class="sxs-lookup"><span data-stu-id="1babb-129">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="1babb-130">當檔案 I/O 完成時，此方法會在 await 陳述式後面的陳述式繼續進行。</span><span class="sxs-lookup"><span data-stu-id="1babb-130">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="1babb-131">Async 修飾詞位於使用 await 語句的方法定義中。</span><span class="sxs-lookup"><span data-stu-id="1babb-131">The async modifier is in the definition of methods that use the await statement.</span></span>

### <a name="simple-example"></a><span data-ttu-id="1babb-132">簡單範例</span><span class="sxs-lookup"><span data-stu-id="1babb-132">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleWrite":::

### <a name="finite-control-example"></a><span data-ttu-id="1babb-133">有限控制項範例</span><span class="sxs-lookup"><span data-stu-id="1babb-133">Finite control example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="WriteText":::

<span data-ttu-id="1babb-134">原始範例具有陳述式 `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`，這是下列兩個陳述式的縮減：</span><span class="sxs-lookup"><span data-stu-id="1babb-134">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>

```csharp
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);
await theTask;
```

<span data-ttu-id="1babb-135">第一個陳述式會傳回一個工作並開始處理檔案。</span><span class="sxs-lookup"><span data-stu-id="1babb-135">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="1babb-136">第二個陳述式具有 await，會立即結束方法並傳回其他工作。</span><span class="sxs-lookup"><span data-stu-id="1babb-136">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="1babb-137">稍後完成處理檔案之後，則會回到 await 後面的陳述式繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1babb-137">When the file processing later completes, execution returns to the statement that follows the await.</span></span>

## <a name="read-text"></a><span data-ttu-id="1babb-138">讀取文字</span><span class="sxs-lookup"><span data-stu-id="1babb-138">Read text</span></span>

<span data-ttu-id="1babb-139">下列範例會從檔案讀取文字。</span><span class="sxs-lookup"><span data-stu-id="1babb-139">The following examples read text from a file.</span></span>

### <a name="simple-example"></a><span data-ttu-id="1babb-140">簡單範例</span><span class="sxs-lookup"><span data-stu-id="1babb-140">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleRead":::

### <a name="finite-control-example"></a><span data-ttu-id="1babb-141">有限控制項範例</span><span class="sxs-lookup"><span data-stu-id="1babb-141">Finite control example</span></span>

<span data-ttu-id="1babb-142">此文字已經過緩衝處理，在本例中已置於 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="1babb-142">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="1babb-143">不同於上一個範例，await 的評估會產生一個值。</span><span class="sxs-lookup"><span data-stu-id="1babb-143">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="1babb-144">方法會傳回 <xref:System.IO.Stream.ReadAsync%2A> <xref:System.Threading.Tasks.Task> \<<xref:System.Int32>>，因此在作業完成之後，await 的評估會產生 `Int32` 值 `numRead` 。</span><span class="sxs-lookup"><span data-stu-id="1babb-144">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value `numRead` after the operation completes.</span></span> <span data-ttu-id="1babb-145">如需詳細資訊，請參閱[非同步方法的傳回型別 (C#)](async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1babb-145">For more information, see [Async Return Types (C#)](async-return-types.md).</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="ReadText":::

## <a name="parallel-asynchronous-io"></a><span data-ttu-id="1babb-146">平行非同步 i/o</span><span class="sxs-lookup"><span data-stu-id="1babb-146">Parallel asynchronous I/O</span></span>

<span data-ttu-id="1babb-147">下列範例示範如何撰寫10個文字檔來進行平行處理。</span><span class="sxs-lookup"><span data-stu-id="1babb-147">The following examples demonstrate parallel processing by writing 10 text files.</span></span>

### <a name="simple-example"></a><span data-ttu-id="1babb-148">簡單範例</span><span class="sxs-lookup"><span data-stu-id="1babb-148">Simple example</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="SimpleParallelWrite":::

### <a name="finite-control-example"></a><span data-ttu-id="1babb-149">有限控制項範例</span><span class="sxs-lookup"><span data-stu-id="1babb-149">Finite control example</span></span>

<span data-ttu-id="1babb-150">針對每個檔案，<xref:System.IO.Stream.WriteAsync%2A> 方法會傳回一個工作，此工作之後會新增至工作清單。</span><span class="sxs-lookup"><span data-stu-id="1babb-150">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="1babb-151">`await Task.WhenAll(tasks);` 陳述式會在所有工作的檔案處理完成時結束方法，並在方法內繼續進行。</span><span class="sxs-lookup"><span data-stu-id="1babb-151">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>

<span data-ttu-id="1babb-152">此範例會在工作完成之後，關閉 `finally` 區塊中的所有 <xref:System.IO.FileStream> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="1babb-152">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="1babb-153">如果改為在 `using` 陳述式中建立每個 `FileStream`，`FileStream` 可能會在工作完成前就被處置。</span><span class="sxs-lookup"><span data-stu-id="1babb-153">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>

<span data-ttu-id="1babb-154">任何效能提升幾乎都是從平行處理，而不是非同步處理。</span><span class="sxs-lookup"><span data-stu-id="1babb-154">Any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="1babb-155">非同步優點在於它不會佔用多個執行緒，也不會佔用使用者介面執行緒。</span><span class="sxs-lookup"><span data-stu-id="1babb-155">The advantages of asynchrony are that it doesn't tie up multiple threads, and that it doesn't tie up the user interface thread.</span></span>

:::code language="csharp" source="snippets/file-access/Program.cs" id="ParallelWriteText":::

<span data-ttu-id="1babb-156">使用 <xref:System.IO.Stream.WriteAsync%2A> 和 <xref:System.IO.Stream.ReadAsync%2A> 方法時，您可以指定 <xref:System.Threading.CancellationToken>，這可用來在中途取消作業。</span><span class="sxs-lookup"><span data-stu-id="1babb-156">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="1babb-157">如需詳細資訊，請參閱 [managed 執行緒中的取消](../../../../standard/threading/cancellation-in-managed-threads.md)。</span><span class="sxs-lookup"><span data-stu-id="1babb-157">For more information, see [Cancellation in managed threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1babb-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1babb-158">See also</span></span>

- [<span data-ttu-id="1babb-159">使用 async 和 await 進行非同步程式設計 (c # ) </span><span class="sxs-lookup"><span data-stu-id="1babb-159">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="1babb-160">非同步傳回類型 (c # ) </span><span class="sxs-lookup"><span data-stu-id="1babb-160">Async return types (C#)</span></span>](async-return-types.md)
