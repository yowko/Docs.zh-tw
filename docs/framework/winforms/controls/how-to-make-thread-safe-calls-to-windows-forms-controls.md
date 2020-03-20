---
title: 對控制項進行執行緒安全調用
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
ms.openlocfilehash: 365b1acb693b9ff2be603a3e659ed8d846a7696a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142000"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="60d4a-102">如何：對 Windows 表單控制項進行執行緒安全調用</span><span class="sxs-lookup"><span data-stu-id="60d4a-102">How to: Make thread-safe calls to Windows Forms controls</span></span>

<span data-ttu-id="60d4a-103">多執行緒可以提高 Windows 表單應用的性能，但訪問 Windows 表單控制項本質上並不安全線程。</span><span class="sxs-lookup"><span data-stu-id="60d4a-103">Multithreading can improve the performance of Windows Forms apps, but access to Windows Forms controls isn't inherently thread-safe.</span></span> <span data-ttu-id="60d4a-104">多執行緒可能會將代碼暴露給非常嚴重和複雜的錯誤。</span><span class="sxs-lookup"><span data-stu-id="60d4a-104">Multithreading can expose your code to very serious and complex bugs.</span></span> <span data-ttu-id="60d4a-105">操作控制項的兩個或多個執行緒可能會強制控制項進入不一致狀態，並導致競爭條件、鎖死以及凍結或掛起。</span><span class="sxs-lookup"><span data-stu-id="60d4a-105">Two or more threads manipulating a control can force the control into an inconsistent state and lead to race conditions, deadlocks, and freezes or hangs.</span></span> <span data-ttu-id="60d4a-106">如果在應用中實現多執行緒讀取，請確保以執行緒安全的方式調用交叉執行緒控制項。</span><span class="sxs-lookup"><span data-stu-id="60d4a-106">If you implement multithreading in your app, be sure to call cross-thread controls in a thread-safe way.</span></span> <span data-ttu-id="60d4a-107">有關詳細資訊，請參閱[託管執行緒最佳實踐](../../../standard/threading/managed-threading-best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="60d4a-107">For more information, see [Managed threading best practices](../../../standard/threading/managed-threading-best-practices.md).</span></span>

<span data-ttu-id="60d4a-108">有兩種方法可以從未創建該控制項的執行緒安全地調用 Windows 表單控制項。</span><span class="sxs-lookup"><span data-stu-id="60d4a-108">There are two ways to safely call a Windows Forms control from a thread that didn't create that control.</span></span> <span data-ttu-id="60d4a-109">可以使用 方法<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>調用在主執行緒中創建的委託，而主執行緒又調用控制項。</span><span class="sxs-lookup"><span data-stu-id="60d4a-109">You can use the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method to call a delegate created in the main thread, which in turn calls the control.</span></span> <span data-ttu-id="60d4a-110">或者，可以實現 一<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>個 ，它使用事件驅動的模型將後臺執行緒中完成的工作與報告結果分開。</span><span class="sxs-lookup"><span data-stu-id="60d4a-110">Or, you can implement a <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, which uses an event-driven model to separate work done in the background thread from reporting on the results.</span></span>

## <a name="unsafe-cross-thread-calls"></a><span data-ttu-id="60d4a-111">不安全的交叉執行緒調用</span><span class="sxs-lookup"><span data-stu-id="60d4a-111">Unsafe cross-thread calls</span></span>

<span data-ttu-id="60d4a-112">直接從未創建控制項的執行緒調用控制項是不安全的。</span><span class="sxs-lookup"><span data-stu-id="60d4a-112">It's unsafe to call a control directly from a thread that didn't create it.</span></span> <span data-ttu-id="60d4a-113">以下程式碼片段說明了對控制項的<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>不安全調用。</span><span class="sxs-lookup"><span data-stu-id="60d4a-113">The following code snippet illustrates an unsafe call to the <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> control.</span></span> <span data-ttu-id="60d4a-114">事件`Button1_Click`處理常式創建一個新`WriteTextUnsafe`執行緒，該執行緒直接設置主執行緒的屬性。 <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="60d4a-114">The `Button1_Click` event handler creates a new `WriteTextUnsafe` thread, which sets the main thread's <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> property directly.</span></span>

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

<span data-ttu-id="60d4a-115">Visual Studio 調試器通過引發消息中的 調用<xref:System.InvalidOperationException>來檢測這些不安全的執行緒調用，**跨執行緒操作無效。控制項""從創建該執行緒以外的執行緒訪問。**</span><span class="sxs-lookup"><span data-stu-id="60d4a-115">The Visual Studio debugger detects these unsafe thread calls by raising an <xref:System.InvalidOperationException> with the message, **Cross-thread operation not valid. Control "" accessed from a thread other than the thread it was created on.**</span></span> <span data-ttu-id="60d4a-116">在<xref:System.InvalidOperationException>Visual Studio 調試期間，始終發生不安全的交叉執行緒調用，並且可能在應用運行時發生。</span><span class="sxs-lookup"><span data-stu-id="60d4a-116">The <xref:System.InvalidOperationException> always occurs for unsafe cross-thread calls during Visual Studio debugging, and may occur at app runtime.</span></span> <span data-ttu-id="60d4a-117">應修復此問題，但可以通過將<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>屬性設置為`false`來禁用異常。</span><span class="sxs-lookup"><span data-stu-id="60d4a-117">You should fix the issue, but you can disable the exception by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> property to `false`.</span></span>

## <a name="safe-cross-thread-calls"></a><span data-ttu-id="60d4a-118">安全交叉執行緒調用</span><span class="sxs-lookup"><span data-stu-id="60d4a-118">Safe cross-thread calls</span></span>

<span data-ttu-id="60d4a-119">以下代碼示例演示了從未創建該控制項的執行緒安全地調用 Windows 表單控制項的兩種方法：</span><span class="sxs-lookup"><span data-stu-id="60d4a-119">The following code examples demonstrate two ways to safely call a Windows Forms control from a thread that didn't create it:</span></span>

1. <span data-ttu-id="60d4a-120">方法<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>，它從主執行緒調用委託來調用控制項。</span><span class="sxs-lookup"><span data-stu-id="60d4a-120">The <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> method, which calls a delegate from the main thread to call the control.</span></span>
2. <span data-ttu-id="60d4a-121">提供<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>事件驅動模型的元件。</span><span class="sxs-lookup"><span data-stu-id="60d4a-121">A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which offers an event-driven model.</span></span>

<span data-ttu-id="60d4a-122">在這兩個示例中，後臺執行緒休眠一秒鐘以類比該執行緒中正在完成的工作。</span><span class="sxs-lookup"><span data-stu-id="60d4a-122">In both examples, the background thread sleeps for one second to simulate work being done in that thread.</span></span>

<span data-ttu-id="60d4a-123">可以從 C# 或 Visual Basic 命令列生成和運行這些示例為 .NET 框架應用。</span><span class="sxs-lookup"><span data-stu-id="60d4a-123">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="60d4a-124">有關詳細資訊，請參閱使用[csc.exe 的命令列構建](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[命令列（可視基本）中的生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="60d4a-124">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="60d4a-125">從 .NET Core 3.0 開始，您還可以從具有 .NET 核心 Windows 表單*\<資料夾名稱>.csproj*專案檔案的資料夾中生成並運行 Windows .NET Core 應用示例。</span><span class="sxs-lookup"><span data-stu-id="60d4a-125">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-use-the-invoke-method-with-a-delegate"></a><span data-ttu-id="60d4a-126">示例：使用具有委託的 Invoke 方法</span><span class="sxs-lookup"><span data-stu-id="60d4a-126">Example: Use the Invoke method with a delegate</span></span>

<span data-ttu-id="60d4a-127">下面的示例演示了用於確保對 Windows 表單控制項進行執行緒安全調用的模式。</span><span class="sxs-lookup"><span data-stu-id="60d4a-127">The following example demonstrates a pattern for ensuring thread-safe calls to a Windows Forms control.</span></span> <span data-ttu-id="60d4a-128">它查詢該<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>屬性，該屬性將控制項的創建執行緒 ID 與調用執行緒 ID 進行比較。</span><span class="sxs-lookup"><span data-stu-id="60d4a-128">It queries the <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> property, which compares the control's creating thread ID to the calling thread ID.</span></span> <span data-ttu-id="60d4a-129">如果執行緒指示相同，它將直接調用控制項。</span><span class="sxs-lookup"><span data-stu-id="60d4a-129">If the thread IDs are the same, it calls the control directly.</span></span> <span data-ttu-id="60d4a-130">如果執行緒指示不同，它將使用主執行緒的委託調用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>方法，從而對控制項進行實際調用。</span><span class="sxs-lookup"><span data-stu-id="60d4a-130">If the thread IDs are different, it calls the <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> method with a delegate from the main thread, which makes the actual call to the control.</span></span>

<span data-ttu-id="60d4a-131">啟用`SafeCallDelegate`設置<xref:System.Windows.Forms.TextBox>控制項的屬性<xref:System.Windows.Forms.TextBox.Text%2A>。</span><span class="sxs-lookup"><span data-stu-id="60d4a-131">The `SafeCallDelegate` enables setting the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="60d4a-132">方法`WriteTextSafe`查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A>。</span><span class="sxs-lookup"><span data-stu-id="60d4a-132">The `WriteTextSafe` method queries <xref:System.Windows.Forms.Control.InvokeRequired%2A>.</span></span> <span data-ttu-id="60d4a-133">如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>返回`true` `WriteTextSafe` ，則`SafeCallDelegate`將<xref:System.Windows.Forms.Control.Invoke%2A>傳遞給 方法以對控制項進行實際調用。</span><span class="sxs-lookup"><span data-stu-id="60d4a-133">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, `WriteTextSafe` passes the `SafeCallDelegate` to the <xref:System.Windows.Forms.Control.Invoke%2A> method to make the actual call to the control.</span></span> <span data-ttu-id="60d4a-134">如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>返回`false` `WriteTextSafe` ，則<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接設置 。</span><span class="sxs-lookup"><span data-stu-id="60d4a-134">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, `WriteTextSafe` sets the <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> directly.</span></span> <span data-ttu-id="60d4a-135">事件`Button1_Click`處理常式創建新執行緒並運行方法`WriteTextSafe`。</span><span class="sxs-lookup"><span data-stu-id="60d4a-135">The `Button1_Click` event handler creates the new thread and runs the `WriteTextSafe` method.</span></span>

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a><span data-ttu-id="60d4a-136">示例：使用後臺輔助角色事件處理常式</span><span class="sxs-lookup"><span data-stu-id="60d4a-136">Example: Use a BackgroundWorker event handler</span></span>

<span data-ttu-id="60d4a-137">實現多執行緒的一種簡單方法是使用<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，該元件使用事件驅動的模型。</span><span class="sxs-lookup"><span data-stu-id="60d4a-137">An easy way to implement multithreading is with the <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> component, which uses an event-driven model.</span></span> <span data-ttu-id="60d4a-138">後臺執行緒運行事件<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>，該事件不與主執行緒交互。</span><span class="sxs-lookup"><span data-stu-id="60d4a-138">The background thread runs the <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> event, which doesn't interact with the main thread.</span></span> <span data-ttu-id="60d4a-139">主執行緒運行 和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType><xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>事件處理常式，可以調用主執行緒的控制項。</span><span class="sxs-lookup"><span data-stu-id="60d4a-139">The main thread runs the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> event handlers, which can call the main thread's controls.</span></span>

<span data-ttu-id="60d4a-140">要使用 進行<xref:System.ComponentModel.BackgroundWorker>執行緒安全調用，請在後臺執行緒中創建一個方法來執行該工作，並將其綁定到<xref:System.ComponentModel.BackgroundWorker.DoWork>事件。</span><span class="sxs-lookup"><span data-stu-id="60d4a-140">To make a thread-safe call by using <xref:System.ComponentModel.BackgroundWorker>, create a method in the background thread to do the work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event.</span></span> <span data-ttu-id="60d4a-141">在主執行緒中創建另一種方法以報告後臺工作的結果，並將其綁定到<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>或<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。</span><span class="sxs-lookup"><span data-stu-id="60d4a-141">Create another method in the main thread to report the results of the background work, and bind it to the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> or <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span> <span data-ttu-id="60d4a-142">要啟動後臺執行緒，請調用<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="60d4a-142">To start the background thread, call <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="60d4a-143">該示例使用<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式設置<xref:System.Windows.Forms.TextBox>控制項的屬性。 <xref:System.Windows.Forms.TextBox.Text%2A></span><span class="sxs-lookup"><span data-stu-id="60d4a-143">The example uses the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler to set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="60d4a-144">有關使用事件的示例，<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>請參閱<xref:System.ComponentModel.BackgroundWorker>。</span><span class="sxs-lookup"><span data-stu-id="60d4a-144">For an example using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span>

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="60d4a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60d4a-145">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="60d4a-146">操作方式：在後臺運行操作</span><span class="sxs-lookup"><span data-stu-id="60d4a-146">How to: Run an operation in the background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="60d4a-147">如何：實現使用後臺操作的表單</span><span class="sxs-lookup"><span data-stu-id="60d4a-147">How to: Implement a form that uses a background operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="60d4a-148">使用 .NET 框架開發自訂 Windows 表單控制項</span><span class="sxs-lookup"><span data-stu-id="60d4a-148">Develop custom Windows Forms controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
