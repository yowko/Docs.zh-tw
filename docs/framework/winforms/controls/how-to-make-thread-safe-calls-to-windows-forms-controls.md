---
title: 對控制項進行安全線程呼叫
ms.date: 02/19/2019
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: 101457ab2a02b8de49d06c354ca307e07b690ba2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736158"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="df4dc-102">如何：對 Windows Forms 控制項進行安全線程呼叫</span><span class="sxs-lookup"><span data-stu-id="df4dc-102">How to: Make thread-safe calls to Windows Forms controls</span></span>

<span data-ttu-id="df4dc-103">多執行緒可以改善 Windows Forms 應用程式的效能，但 Windows Forms 控制項的存取原本就不是安全線程。</span><span class="sxs-lookup"><span data-stu-id="df4dc-103">Multithreading can improve the performance of Windows Forms apps, but access to Windows Forms controls isn't inherently thread-safe.</span></span> <span data-ttu-id="df4dc-104">多執行緒可以將您的程式碼公開給非常嚴重且複雜的 bug。</span><span class="sxs-lookup"><span data-stu-id="df4dc-104">Multithreading can expose your code to very serious and complex bugs.</span></span> <span data-ttu-id="df4dc-105">操控控制項的兩個或多個執行緒可以強制控制項進入不一致的狀態，並導致競爭情況、鎖死、凍結或停止回應。</span><span class="sxs-lookup"><span data-stu-id="df4dc-105">Two or more threads manipulating a control can force the control into an inconsistent state and lead to race conditions, deadlocks, and freezes or hangs.</span></span> <span data-ttu-id="df4dc-106">如果您在應用程式中執行多執行緒處理，請務必以執行緒安全的方式呼叫跨執行緒控制項。</span><span class="sxs-lookup"><span data-stu-id="df4dc-106">If you implement multithreading in your app, be sure to call cross-thread controls in a thread-safe way.</span></span> <span data-ttu-id="df4dc-107">如需詳細資訊，請參閱[Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="df4dc-107">For more information, see [Managed threading best practices](../../../standard/threading/managed-threading-best-practices.md).</span></span> 

<span data-ttu-id="df4dc-108">有兩種方式可以從未建立該控制項的執行緒安全地呼叫 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="df4dc-108">There are two ways to safely call a Windows Forms control from a thread that didn't create that control.</span></span> <span data-ttu-id="df4dc-109">您可以使用 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 方法來呼叫在主執行緒中建立的委派，然後再呼叫該控制項。</span><span class="sxs-lookup"><span data-stu-id="df4dc-109">You can use the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method to call a delegate created in the main thread, which in turn calls the control.</span></span> <span data-ttu-id="df4dc-110">或者，您可以執行 <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>，它會使用事件驅動模型來分隔背景執行緒中完成的工作，使其不會報告結果。</span><span class="sxs-lookup"><span data-stu-id="df4dc-110">Or, you can implement a <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, which uses an event-driven model to separate work done in the background thread from reporting on the results.</span></span> 

## <a name="unsafe-cross-thread-calls"></a><span data-ttu-id="df4dc-111">不安全的跨執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="df4dc-111">Unsafe cross-thread calls</span></span>

<span data-ttu-id="df4dc-112">不安全的方式是直接從未建立的執行緒呼叫控制項。</span><span class="sxs-lookup"><span data-stu-id="df4dc-112">It's unsafe to call a control directly from a thread that didn't create it.</span></span> <span data-ttu-id="df4dc-113">下列程式碼片段說明對 <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> 控制項的不安全呼叫。</span><span class="sxs-lookup"><span data-stu-id="df4dc-113">The following code snippet illustrates an unsafe call to the <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> control.</span></span> <span data-ttu-id="df4dc-114">`Button1_Click` 事件處理常式會建立新的 `WriteTextUnsafe` 執行緒，這會直接設定主執行緒的 <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="df4dc-114">The `Button1_Click` event handler creates a new `WriteTextUnsafe` thread, which sets the main thread's <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> property directly.</span></span> 

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

<span data-ttu-id="df4dc-115">Visual Studio 偵錯工具會藉由引發包含訊息的 <xref:System.InvalidOperationException>，跨執行緒作業無效來偵測這些不安全的執行緒呼叫 **。控制項 "" 是從建立它**的執行緒以外的執行緒存取。</span><span class="sxs-lookup"><span data-stu-id="df4dc-115">The Visual Studio debugger detects these unsafe thread calls by raising an <xref:System.InvalidOperationException> with the message, **Cross-thread operation not valid. Control "" accessed from a thread other than the thread it was created on.**</span></span> <span data-ttu-id="df4dc-116">在 Visual Studio 調試期間，不安全的跨執行緒呼叫一律會發生 <xref:System.InvalidOperationException>，而且可能會在應用程式執行時間發生。</span><span class="sxs-lookup"><span data-stu-id="df4dc-116">The <xref:System.InvalidOperationException> always occurs for unsafe cross-thread calls during Visual Studio debugging, and may occur at app runtime.</span></span> <span data-ttu-id="df4dc-117">您應該修正此問題，但您可以將 [<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>] 屬性設定為 [`false`] 來停用例外狀況。</span><span class="sxs-lookup"><span data-stu-id="df4dc-117">You should fix the issue, but you can disable the exception by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> property to `false`.</span></span>

## <a name="safe-cross-thread-calls"></a><span data-ttu-id="df4dc-118">安全的跨執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="df4dc-118">Safe cross-thread calls</span></span> 

<span data-ttu-id="df4dc-119">下列程式碼範例示範兩種安全地從未建立的執行緒呼叫 Windows Forms 控制項的方式：</span><span class="sxs-lookup"><span data-stu-id="df4dc-119">The following code examples demonstrate two ways to safely call a Windows Forms control from a thread that didn't create it:</span></span> 

1. <span data-ttu-id="df4dc-120"><xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 方法，它會從主執行緒呼叫委派以呼叫控制項。</span><span class="sxs-lookup"><span data-stu-id="df4dc-120">The <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method, which calls a delegate from the main thread to call the control.</span></span> 
2. <span data-ttu-id="df4dc-121"><xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 元件，提供事件驅動模型。</span><span class="sxs-lookup"><span data-stu-id="df4dc-121">A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which offers an event-driven model.</span></span> 

<span data-ttu-id="df4dc-122">在這兩個範例中，背景執行緒會進入睡眠狀態一秒，以模擬在該執行緒中完成的工作。</span><span class="sxs-lookup"><span data-stu-id="df4dc-122">In both examples, the background thread sleeps for one second to simulate work being done in that thread.</span></span> 

<span data-ttu-id="df4dc-123">您可以從C#或 Visual Basic 命令列，將這些範例建立並執行為 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="df4dc-123">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="df4dc-124">如需詳細資訊，請參閱[使用 ngen.exe 建立命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建立（Visual Basic）](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="df4dc-124">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span> 

<span data-ttu-id="df4dc-125">從 .NET Core 3.0 開始，您也可以從具有 .NET Core Windows Forms 的資料夾中，建立並執行範例做為 Windows .NET Core 應用程式 *\<資料夾名稱 > .csproj*專案檔案。</span><span class="sxs-lookup"><span data-stu-id="df4dc-125">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span> 

## <a name="example-use-the-invoke-method-with-a-delegate"></a><span data-ttu-id="df4dc-126">範例：搭配使用 Invoke 方法與委派</span><span class="sxs-lookup"><span data-stu-id="df4dc-126">Example: Use the Invoke method with a delegate</span></span>

<span data-ttu-id="df4dc-127">下列範例示範的模式可確保對 Windows Forms 控制項的安全線程呼叫。</span><span class="sxs-lookup"><span data-stu-id="df4dc-127">The following example demonstrates a pattern for ensuring thread-safe calls to a Windows Forms control.</span></span> <span data-ttu-id="df4dc-128">它會查詢 <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> 屬性，這會將控制項的建立執行緒識別碼與呼叫執行緒識別碼進行比較。</span><span class="sxs-lookup"><span data-stu-id="df4dc-128">It queries the <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> property, which compares the control's creating thread ID to the calling thread ID.</span></span> <span data-ttu-id="df4dc-129">如果執行緒識別碼相同，它會直接呼叫控制項。</span><span class="sxs-lookup"><span data-stu-id="df4dc-129">If the thread IDs are the same, it calls the control directly.</span></span> <span data-ttu-id="df4dc-130">如果執行緒識別碼不同，它會使用主執行緒的委派呼叫 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> 方法，這會對控制項進行實際呼叫。</span><span class="sxs-lookup"><span data-stu-id="df4dc-130">If the thread IDs are different, it calls the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> method with a delegate from the main thread, which makes the actual call to the control.</span></span>

<span data-ttu-id="df4dc-131">`SafeCallDelegate` 可設定 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="df4dc-131">The `SafeCallDelegate` enables setting the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="df4dc-132">`WriteTextSafe` 的方法查詢 <xref:System.Windows.Forms.Control.InvokeRequired%2A>。</span><span class="sxs-lookup"><span data-stu-id="df4dc-132">The `WriteTextSafe` method queries <xref:System.Windows.Forms.Control.InvokeRequired%2A>.</span></span> <span data-ttu-id="df4dc-133">如果 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 傳回 `true`，`WriteTextSafe` 會將 `SafeCallDelegate` 傳遞至 <xref:System.Windows.Forms.Control.Invoke%2A> 方法，以對控制項進行實際的呼叫。</span><span class="sxs-lookup"><span data-stu-id="df4dc-133">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, `WriteTextSafe` passes the `SafeCallDelegate` to the <xref:System.Windows.Forms.Control.Invoke%2A> method to make the actual call to the control.</span></span> <span data-ttu-id="df4dc-134">如果 <xref:System.Windows.Forms.Control.InvokeRequired%2A> 傳回 `false`，`WriteTextSafe` 會直接設定 <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="df4dc-134">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, `WriteTextSafe` sets the <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> directly.</span></span> <span data-ttu-id="df4dc-135">`Button1_Click` 事件處理常式會建立新的執行緒，並執行 `WriteTextSafe` 方法。</span><span class="sxs-lookup"><span data-stu-id="df4dc-135">The `Button1_Click` event handler creates the new thread and runs the `WriteTextSafe` method.</span></span> 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a><span data-ttu-id="df4dc-136">範例：使用 BackgroundWorker 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="df4dc-136">Example: Use a BackgroundWorker event handler</span></span>

<span data-ttu-id="df4dc-137">執行多執行緒的簡單方法是使用 <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 元件，其使用事件驅動模型。</span><span class="sxs-lookup"><span data-stu-id="df4dc-137">An easy way to implement multithreading is with the <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which uses an event-driven model.</span></span> <span data-ttu-id="df4dc-138">背景執行緒會執行 <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> 事件，這不會與主執行緒互動。</span><span class="sxs-lookup"><span data-stu-id="df4dc-138">The background thread runs the <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> event, which doesn't interact with the main thread.</span></span> <span data-ttu-id="df4dc-139">主要執行緒會執行 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>，並 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> 事件處理常式，以呼叫主執行緒的控制項。</span><span class="sxs-lookup"><span data-stu-id="df4dc-139">The main thread runs the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> event handlers, which can call the main thread's controls.</span></span>

<span data-ttu-id="df4dc-140">若要使用 <xref:System.ComponentModel.BackgroundWorker>建立安全線程呼叫，請在背景執行緒中建立方法來執行工作，並將它系結至 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件。</span><span class="sxs-lookup"><span data-stu-id="df4dc-140">To make a thread-safe call by using <xref:System.ComponentModel.BackgroundWorker>, create a method in the background thread to do the work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event.</span></span> <span data-ttu-id="df4dc-141">在主執行緒中建立另一個方法，以報告背景工作的結果，並將它系結至 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 或 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件。</span><span class="sxs-lookup"><span data-stu-id="df4dc-141">Create another method in the main thread to report the results of the background work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> or <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span> <span data-ttu-id="df4dc-142">若要啟動背景執行緒，請呼叫 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="df4dc-142">To start the background thread, call <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>.</span></span> 

<span data-ttu-id="df4dc-143">這個範例會使用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件處理常式來設定 <xref:System.Windows.Forms.TextBox> 控制項的 <xref:System.Windows.Forms.TextBox.Text%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="df4dc-143">The example uses the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler to set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="df4dc-144">如需使用 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> 事件的範例，請參閱 <xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="df4dc-144">For an example using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span> 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="df4dc-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df4dc-145">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="df4dc-146">如何：在背景中執行作業</span><span class="sxs-lookup"><span data-stu-id="df4dc-146">How to: Run an operation in the background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="df4dc-147">如何：執行使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="df4dc-147">How to: Implement a form that uses a background operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="df4dc-148">使用 .NET Framework 開發自訂 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="df4dc-148">Develop custom Windows Forms controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
