---
title: HOW TO：進行對 Windows Form 控制項的安全執行緒呼叫
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
ms.openlocfilehash: ef7836721df6c090a4d09c38c176641331c3e8a4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362561"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="5f940-102">HOW TO：進行對 Windows Form 控制項的安全執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="5f940-102">How to: Make thread-safe calls to Windows Forms controls</span></span>

<span data-ttu-id="5f940-103">多執行緒可以改善效能的 Windows Forms 應用程式，但存取 Windows Form 控制項不是原本就是執行緒安全。</span><span class="sxs-lookup"><span data-stu-id="5f940-103">Multithreading can improve the performance of Windows Forms apps, but access to Windows Forms controls isn't inherently thread-safe.</span></span> <span data-ttu-id="5f940-104">多執行緒可以公開您的程式碼非常嚴重且複雜的錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f940-104">Multithreading can expose your code to very serious and complex bugs.</span></span> <span data-ttu-id="5f940-105">管理控制項的兩個或多個執行緒可以強制控制項進入不一致的狀態，並會導致競爭情況、 死結和凍結或停止回應。</span><span class="sxs-lookup"><span data-stu-id="5f940-105">Two or more threads manipulating a control can force the control into an inconsistent state and lead to race conditions, deadlocks, and freezes or hangs.</span></span> <span data-ttu-id="5f940-106">如果您實作多執行緒在您的應用程式，務必以安全執行緒方式呼叫跨執行緒的控制項。</span><span class="sxs-lookup"><span data-stu-id="5f940-106">If you implement multithreading in your app, be sure to call cross-thread controls in a thread-safe way.</span></span> <span data-ttu-id="5f940-107">如需詳細資訊，請參閱 < [Managed 執行緒最佳做法](../../../../docs/standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="5f940-107">For more information, see [Managed threading best practices](../../../../docs/standard/threading/managed-threading-best-practices.md).</span></span> 

<span data-ttu-id="5f940-108">有兩種方式可安全地從未建立該控制項的執行緒中呼叫的 Windows Form 控制項。</span><span class="sxs-lookup"><span data-stu-id="5f940-108">There are two ways to safely call a Windows Forms control from a thread that didn't create that control.</span></span> <span data-ttu-id="5f940-109">您可以使用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法來呼叫在主執行緒，也就會呼叫控制項中建立的委派。</span><span class="sxs-lookup"><span data-stu-id="5f940-109">You can use the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method to call a delegate created in the main thread, which in turn calls the control.</span></span> <span data-ttu-id="5f940-110">或者，您可以實作<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>，這會使用事件驅動的模型來分隔結果報告在背景執行緒完成工作。</span><span class="sxs-lookup"><span data-stu-id="5f940-110">Or, you can implement a <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, which uses an event-driven model to separate work done in the background thread from reporting on the results.</span></span> 

## <a name="unsafe-cross-thread-calls"></a><span data-ttu-id="5f940-111">不安全的跨執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="5f940-111">Unsafe cross-thread calls</span></span>

<span data-ttu-id="5f940-112">它並不安全呼叫控制項，直接從未建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5f940-112">It's unsafe to call a control directly from a thread that didn't create it.</span></span> <span data-ttu-id="5f940-113">下列程式碼片段會示範不安全的對<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>控制項。</span><span class="sxs-lookup"><span data-stu-id="5f940-113">The following code snippet illustrates an unsafe call to the <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> control.</span></span> <span data-ttu-id="5f940-114">`Button1_Click`事件處理常式建立新`WriteTextUnsafe`設定的主執行緒的執行緒<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接屬性。</span><span class="sxs-lookup"><span data-stu-id="5f940-114">The `Button1_Click` event handler creates a new `WriteTextUnsafe` thread, which sets the main thread's <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> property directly.</span></span> 

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

<span data-ttu-id="5f940-115">Visual Studio 偵錯工具偵測到這些不安全的執行緒呼叫，藉由引發<xref:System.InvalidOperationException>訊息：**跨執行緒作業無效。控制 「 」 從其所建立的執行緒以外的執行緒存取。**</span><span class="sxs-lookup"><span data-stu-id="5f940-115">The Visual Studio debugger detects these unsafe thread calls by raising an <xref:System.InvalidOperationException> with the message, **Cross-thread operation not valid. Control "" accessed from a thread other than the thread it was created on.**</span></span> <span data-ttu-id="5f940-116"><xref:System.InvalidOperationException>永遠不安全的跨執行緒呼叫 Visual Studio 偵錯時，就會發生，而且可能會發生在應用程式執行階段。</span><span class="sxs-lookup"><span data-stu-id="5f940-116">The <xref:System.InvalidOperationException> always occurs for unsafe cross-thread calls during Visual Studio debugging, and may occur at app runtime.</span></span> <span data-ttu-id="5f940-117">您應該修正問題，但您可以設定連線，停用例外狀況<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="5f940-117">You should fix the issue, but you can disable the exception by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> property to `false`.</span></span>

## <a name="safe-cross-thread-calls"></a><span data-ttu-id="5f940-118">安全的跨執行緒呼叫</span><span class="sxs-lookup"><span data-stu-id="5f940-118">Safe cross-thread calls</span></span> 

<span data-ttu-id="5f940-119">下列程式碼範例示範兩種方式可安全地從未建立的執行緒中呼叫的 Windows Form 控制項：</span><span class="sxs-lookup"><span data-stu-id="5f940-119">The following code examples demonstrate two ways to safely call a Windows Forms control from a thread that didn't create it:</span></span> 
1. <span data-ttu-id="5f940-120"><xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法，從主執行緒呼叫控制項呼叫委派。</span><span class="sxs-lookup"><span data-stu-id="5f940-120">The <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method, which calls a delegate from the main thread to call the control.</span></span> 
2. <span data-ttu-id="5f940-121">A<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，可提供的事件驅動模型。</span><span class="sxs-lookup"><span data-stu-id="5f940-121">A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which offers an event-driven model.</span></span> 

<span data-ttu-id="5f940-122">在這兩個範例中，以模擬一秒背景執行緒會休眠工作在該執行緒中完成。</span><span class="sxs-lookup"><span data-stu-id="5f940-122">In both examples, the background thread sleeps for one second to simulate work being done in that thread.</span></span> 

<span data-ttu-id="5f940-123">您可以建置並執行這些範例做為.NET Framework 應用程式，從C#或 Visual Basic 命令列。</span><span class="sxs-lookup"><span data-stu-id="5f940-123">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="5f940-124">如需詳細資訊，請參閱 <<c0> [ 使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或是[從命令列 (Visual Basic) 建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="5f940-124">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span> 

<span data-ttu-id="5f940-125">從.NET Core 3.0 開始，您可以也建立並執行範例當做 Windows.NET Core 應用程式從資料夾具有.NET Core 的 Windows Forms *\<資料夾名稱 >.csproj*專案檔。</span><span class="sxs-lookup"><span data-stu-id="5f940-125">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span> 

## <a name="example-use-the-invoke-method-with-a-delegate"></a><span data-ttu-id="5f940-126">範例：使用委派的叫用方法</span><span class="sxs-lookup"><span data-stu-id="5f940-126">Example: Use the Invoke method with a delegate</span></span>

<span data-ttu-id="5f940-127">下列範例示範以確保安全執行緒呼叫至 Windows Form 控制項的模式。</span><span class="sxs-lookup"><span data-stu-id="5f940-127">The following example demonstrates a pattern for ensuring thread-safe calls to a Windows Forms control.</span></span> <span data-ttu-id="5f940-128">它會查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>屬性，它會比較控制項的建立執行緒 ID，以呼叫的執行緒 id。</span><span class="sxs-lookup"><span data-stu-id="5f940-128">It queries the <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> property, which compares the control's creating thread ID to the calling thread ID.</span></span> <span data-ttu-id="5f940-129">如果執行緒識別碼都相同，則會呼叫控制項直接。</span><span class="sxs-lookup"><span data-stu-id="5f940-129">If the thread IDs are the same, it calls the control directly.</span></span> <span data-ttu-id="5f940-130">如果執行緒識別碼不同，它會呼叫<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>從主執行緒，讓控制項實際呼叫的委派的方法。</span><span class="sxs-lookup"><span data-stu-id="5f940-130">If the thread IDs are different, it calls the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> method with a delegate from the main thread, which makes the actual call to the control.</span></span>

<span data-ttu-id="5f940-131">`SafeCallDelegate`可讓設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="5f940-131">The `SafeCallDelegate` enables setting the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="5f940-132">`WriteTextSafe`方法查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A>。</span><span class="sxs-lookup"><span data-stu-id="5f940-132">The `WriteTextSafe` method queries <xref:System.Windows.Forms.Control.InvokeRequired%2A>.</span></span> <span data-ttu-id="5f940-133">如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>會傳回`true`，`WriteTextSafe`傳遞`SafeCallDelegate`到<xref:System.Windows.Forms.Control.Invoke%2A>進行控制項實際呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="5f940-133">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, `WriteTextSafe` passes the `SafeCallDelegate` to the <xref:System.Windows.Forms.Control.Invoke%2A> method to make the actual call to the control.</span></span> <span data-ttu-id="5f940-134">如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>會傳回`false`，`WriteTextSafe`設定<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接。</span><span class="sxs-lookup"><span data-stu-id="5f940-134">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, `WriteTextSafe` sets the <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> directly.</span></span> <span data-ttu-id="5f940-135">`Button1_Click`事件處理常式會建立新的執行緒，並執行`WriteTextSafe`方法。</span><span class="sxs-lookup"><span data-stu-id="5f940-135">The `Button1_Click` event handler creates the new thread and runs the `WriteTextSafe` method.</span></span> 

 [!code-csharp[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a><span data-ttu-id="5f940-136">範例：使用 BackgroundWorker 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="5f940-136">Example: Use a BackgroundWorker event handler</span></span>

<span data-ttu-id="5f940-137">輕鬆地實作多執行緒是使用<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，可使用事件驅動的模型。</span><span class="sxs-lookup"><span data-stu-id="5f940-137">An easy way to implement multithreading is with the <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which uses an event-driven model.</span></span> <span data-ttu-id="5f940-138">背景執行緒會執行<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>事件，不會與主執行緒互動。</span><span class="sxs-lookup"><span data-stu-id="5f940-138">The background thread runs the <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> event, which doesn't interact with the main thread.</span></span> <span data-ttu-id="5f940-139">主要執行緒會執行<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>事件處理常式，可以呼叫主執行緒的控制項。</span><span class="sxs-lookup"><span data-stu-id="5f940-139">The main thread runs the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> event handlers, which can call the main thread's controls.</span></span>

<span data-ttu-id="5f940-140">若要使用時，進行安全執行緒呼叫<xref:System.ComponentModel.BackgroundWorker>、 在背景執行緒執行工作，建立一個方法，並繫結至<xref:System.ComponentModel.BackgroundWorker.DoWork>事件。</span><span class="sxs-lookup"><span data-stu-id="5f940-140">To make a thread-safe call by using <xref:System.ComponentModel.BackgroundWorker>, create a method in the background thread to do the work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event.</span></span> <span data-ttu-id="5f940-141">在主執行緒報告的背景工作，結果中建立另一個方法，並繫結至<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>或<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="5f940-141">Create another method in the main thread to report the results of the background work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> or <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span> <span data-ttu-id="5f940-142">若要啟動背景執行緒，請呼叫<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5f940-142">To start the background thread, call <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>.</span></span> 

<span data-ttu-id="5f940-143">此範例會使用<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>若要設定的事件處理常式<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="5f940-143">The example uses the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler to set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="5f940-144">使用範例<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件，請參閱<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="5f940-144">For an example using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span> 

 [!code-csharp[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="5f940-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f940-145">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="5f940-146">如何：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="5f940-146">How to: Run an operation in the background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="5f940-147">如何：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="5f940-147">How to: Implement a form that uses a background operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="5f940-148">開發以.NET Framework 的自訂 Windows Forms 控制項</span><span class="sxs-lookup"><span data-stu-id="5f940-148">Develop custom Windows Forms controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
