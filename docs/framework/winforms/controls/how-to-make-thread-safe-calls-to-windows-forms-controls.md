---
title: 作法：對 Windows Forms 控制項進行安全線程呼叫
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
ms.openlocfilehash: 78ad7b16d5220972a61848c0c80cd884afa842d9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928622"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="00388-102">作法：對 Windows Forms 控制項進行安全線程呼叫</span><span class="sxs-lookup"><span data-stu-id="00388-102">How to: Make thread-safe calls to Windows Forms controls</span></span>

<span data-ttu-id="00388-103">多執行緒可以改善 Windows Forms 應用程式的效能，但 Windows Forms 控制項的存取原本就不是安全線程。</span><span class="sxs-lookup"><span data-stu-id="00388-103">Multithreading can improve the performance of Windows Forms apps, but access to Windows Forms controls isn't inherently thread-safe.</span></span> <span data-ttu-id="00388-104">多執行緒可以將您的程式碼公開給非常嚴重且複雜的 bug。</span><span class="sxs-lookup"><span data-stu-id="00388-104">Multithreading can expose your code to very serious and complex bugs.</span></span> <span data-ttu-id="00388-105">操控控制項的兩個或多個執行緒可以強制控制項進入不一致的狀態，並導致競爭情況、鎖死、凍結或停止回應。</span><span class="sxs-lookup"><span data-stu-id="00388-105">Two or more threads manipulating a control can force the control into an inconsistent state and lead to race conditions, deadlocks, and freezes or hangs.</span></span> <span data-ttu-id="00388-106">如果您在應用程式中執行多執行緒處理，請務必以執行緒安全的方式呼叫跨執行緒控制項。</span><span class="sxs-lookup"><span data-stu-id="00388-106">If you implement multithreading in your app, be sure to call cross-thread controls in a thread-safe way.</span></span> <span data-ttu-id="00388-107">如需詳細資訊，請參閱[Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="00388-107">For more information, see [Managed threading best practices](../../../standard/threading/managed-threading-best-practices.md).</span></span> 

<span data-ttu-id="00388-108">有兩種方式可以從未建立該控制項的執行緒安全地呼叫 Windows Forms 控制項。</span><span class="sxs-lookup"><span data-stu-id="00388-108">There are two ways to safely call a Windows Forms control from a thread that didn't create that control.</span></span> <span data-ttu-id="00388-109">您可以使用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法來呼叫在主執行緒中建立的委派，然後再呼叫該控制項。</span><span class="sxs-lookup"><span data-stu-id="00388-109">You can use the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method to call a delegate created in the main thread, which in turn calls the control.</span></span> <span data-ttu-id="00388-110">或者，您可以執行<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>，它會使用事件驅動模型來分隔背景執行緒中完成的工作，使其無法報告結果。</span><span class="sxs-lookup"><span data-stu-id="00388-110">Or, you can implement a <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, which uses an event-driven model to separate work done in the background thread from reporting on the results.</span></span> 

## <a name="unsafe-cross-thread-calls"></a><span data-ttu-id="00388-111">不安全的跨執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="00388-111">Unsafe cross-thread calls</span></span>

<span data-ttu-id="00388-112">不安全的方式是直接從未建立的執行緒呼叫控制項。</span><span class="sxs-lookup"><span data-stu-id="00388-112">It's unsafe to call a control directly from a thread that didn't create it.</span></span> <span data-ttu-id="00388-113">下列程式碼片段說明對<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>控制項的不安全呼叫。</span><span class="sxs-lookup"><span data-stu-id="00388-113">The following code snippet illustrates an unsafe call to the <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> control.</span></span> <span data-ttu-id="00388-114">事件處理常式會建立新`WriteTextUnsafe`的執行緒，它會直接設定主<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>執行緒的屬性。 `Button1_Click`</span><span class="sxs-lookup"><span data-stu-id="00388-114">The `Button1_Click` event handler creates a new `WriteTextUnsafe` thread, which sets the main thread's <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> property directly.</span></span> 

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

<span data-ttu-id="00388-115">Visual Studio 偵錯工具會藉由引發<xref:System.InvalidOperationException>與訊息， **跨執行緒作業無效來偵測這些不安全的執行緒呼叫。控制項 "" 是從建立它的執行緒以外的執行緒存取。**</span><span class="sxs-lookup"><span data-stu-id="00388-115">The Visual Studio debugger detects these unsafe thread calls by raising an <xref:System.InvalidOperationException> with the message, **Cross-thread operation not valid. Control "" accessed from a thread other than the thread it was created on.**</span></span> <span data-ttu-id="00388-116">在<xref:System.InvalidOperationException> Visual Studio 的調試期間，一律會發生不安全的跨執行緒呼叫，而且可能會在應用程式執行時間發生。</span><span class="sxs-lookup"><span data-stu-id="00388-116">The <xref:System.InvalidOperationException> always occurs for unsafe cross-thread calls during Visual Studio debugging, and may occur at app runtime.</span></span> <span data-ttu-id="00388-117">您應該修正此問題，但您可以藉由將<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>屬性設定為來`false`停用例外狀況。</span><span class="sxs-lookup"><span data-stu-id="00388-117">You should fix the issue, but you can disable the exception by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> property to `false`.</span></span>

## <a name="safe-cross-thread-calls"></a><span data-ttu-id="00388-118">安全的跨執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="00388-118">Safe cross-thread calls</span></span> 

<span data-ttu-id="00388-119">下列程式碼範例示範兩種安全地從未建立的執行緒呼叫 Windows Forms 控制項的方式：</span><span class="sxs-lookup"><span data-stu-id="00388-119">The following code examples demonstrate two ways to safely call a Windows Forms control from a thread that didn't create it:</span></span> 

1. <span data-ttu-id="00388-120"><xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法，它會從主執行緒呼叫委派以呼叫控制項。</span><span class="sxs-lookup"><span data-stu-id="00388-120">The <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method, which calls a delegate from the main thread to call the control.</span></span> 
2. <span data-ttu-id="00388-121"><xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，提供事件驅動模型。</span><span class="sxs-lookup"><span data-stu-id="00388-121">A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which offers an event-driven model.</span></span> 

<span data-ttu-id="00388-122">在這兩個範例中，背景執行緒會進入睡眠狀態一秒，以模擬在該執行緒中完成的工作。</span><span class="sxs-lookup"><span data-stu-id="00388-122">In both examples, the background thread sleeps for one second to simulate work being done in that thread.</span></span> 

<span data-ttu-id="00388-123">您可以從C#或 Visual Basic 命令列，將這些範例建立並執行為 .NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="00388-123">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="00388-124">如需詳細資訊，請參閱[使用 ngen.exe 建立命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建立（Visual Basic）](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="00388-124">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span> 

<span data-ttu-id="00388-125">從 .net core 3.0 開始，您也可以從具有 .net core Windows Forms  *\<資料夾名稱 > .csproj*專案檔的資料夾中，建立並執行範例做為 Windows .net core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="00388-125">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span> 

## <a name="example-use-the-invoke-method-with-a-delegate"></a><span data-ttu-id="00388-126">範例：搭配使用 Invoke 方法與委派</span><span class="sxs-lookup"><span data-stu-id="00388-126">Example: Use the Invoke method with a delegate</span></span>

<span data-ttu-id="00388-127">下列範例示範的模式可確保對 Windows Forms 控制項的安全線程呼叫。</span><span class="sxs-lookup"><span data-stu-id="00388-127">The following example demonstrates a pattern for ensuring thread-safe calls to a Windows Forms control.</span></span> <span data-ttu-id="00388-128">它會查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>屬性，其會將控制項的建立執行緒識別碼與呼叫執行緒識別碼進行比較。</span><span class="sxs-lookup"><span data-stu-id="00388-128">It queries the <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> property, which compares the control's creating thread ID to the calling thread ID.</span></span> <span data-ttu-id="00388-129">如果執行緒識別碼相同，它會直接呼叫控制項。</span><span class="sxs-lookup"><span data-stu-id="00388-129">If the thread IDs are the same, it calls the control directly.</span></span> <span data-ttu-id="00388-130">如果執行緒識別碼不同，則會使用主執行緒<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>的委派來呼叫方法，這會對控制項進行實際的呼叫。</span><span class="sxs-lookup"><span data-stu-id="00388-130">If the thread IDs are different, it calls the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> method with a delegate from the main thread, which makes the actual call to the control.</span></span>

<span data-ttu-id="00388-131">可讓您<xref:System.Windows.Forms.TextBox>設定控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。 `SafeCallDelegate`</span><span class="sxs-lookup"><span data-stu-id="00388-131">The `SafeCallDelegate` enables setting the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="00388-132">`WriteTextSafe`方法查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A>。</span><span class="sxs-lookup"><span data-stu-id="00388-132">The `WriteTextSafe` method queries <xref:System.Windows.Forms.Control.InvokeRequired%2A>.</span></span> <span data-ttu-id="00388-133"><xref:System.Windows.Forms.Control.InvokeRequired%2A> `SafeCallDelegate` 如果傳回<xref:System.Windows.Forms.Control.Invoke%2A> ，則`WriteTextSafe`會將傳遞至方法，以對控制項進行實際的呼叫。 `true`</span><span class="sxs-lookup"><span data-stu-id="00388-133">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, `WriteTextSafe` passes the `SafeCallDelegate` to the <xref:System.Windows.Forms.Control.Invoke%2A> method to make the actual call to the control.</span></span> <span data-ttu-id="00388-134">如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>傳回 ，`WriteTextSafe`則會<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接設定。 `false`</span><span class="sxs-lookup"><span data-stu-id="00388-134">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, `WriteTextSafe` sets the <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> directly.</span></span> <span data-ttu-id="00388-135">事件處理常式會建立新的執行緒，並`WriteTextSafe`執行方法。 `Button1_Click`</span><span class="sxs-lookup"><span data-stu-id="00388-135">The `Button1_Click` event handler creates the new thread and runs the `WriteTextSafe` method.</span></span> 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a><span data-ttu-id="00388-136">範例：使用 BackgroundWorker 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="00388-136">Example: Use a BackgroundWorker event handler</span></span>

<span data-ttu-id="00388-137">執行多執行緒的簡單方法是<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>使用元件，其使用事件驅動模型。</span><span class="sxs-lookup"><span data-stu-id="00388-137">An easy way to implement multithreading is with the <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which uses an event-driven model.</span></span> <span data-ttu-id="00388-138">背景執行緒會執行<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>事件，這不會與主執行緒互動。</span><span class="sxs-lookup"><span data-stu-id="00388-138">The background thread runs the <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> event, which doesn't interact with the main thread.</span></span> <span data-ttu-id="00388-139">主要執行緒會執行<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>事件處理常式，以呼叫主執行緒的控制項。</span><span class="sxs-lookup"><span data-stu-id="00388-139">The main thread runs the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> event handlers, which can call the main thread's controls.</span></span>

<span data-ttu-id="00388-140">若要使用<xref:System.ComponentModel.BackgroundWorker>進行安全線程呼叫，請在背景執行緒中建立方法來執行工作，並將它系結<xref:System.ComponentModel.BackgroundWorker.DoWork>至事件。</span><span class="sxs-lookup"><span data-stu-id="00388-140">To make a thread-safe call by using <xref:System.ComponentModel.BackgroundWorker>, create a method in the background thread to do the work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event.</span></span> <span data-ttu-id="00388-141">在主執行緒中建立另一個方法，以報告背景工作的結果，並將它系結<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>至<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>或事件。</span><span class="sxs-lookup"><span data-stu-id="00388-141">Create another method in the main thread to report the results of the background work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> or <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span> <span data-ttu-id="00388-142">若要啟動背景執行緒，請<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>呼叫。</span><span class="sxs-lookup"><span data-stu-id="00388-142">To start the background thread, call <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>.</span></span> 

<span data-ttu-id="00388-143">這個範例會使用<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式來<xref:System.Windows.Forms.TextBox>設定控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="00388-143">The example uses the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler to set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="00388-144">如需使用<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的範例，請<xref:System.ComponentModel.BackgroundWorker>參閱。</span><span class="sxs-lookup"><span data-stu-id="00388-144">For an example using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span> 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="00388-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00388-145">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="00388-146">如何：在背景中執行作業</span><span class="sxs-lookup"><span data-stu-id="00388-146">How to: Run an operation in the background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="00388-147">如何：執行使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="00388-147">How to: Implement a form that uses a background operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="00388-148">使用 .NET Framework 開發自訂 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="00388-148">Develop custom Windows Forms controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
