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
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>HOW TO：進行對 Windows Form 控制項的安全執行緒呼叫

多執行緒可以改善效能的 Windows Forms 應用程式，但存取 Windows Form 控制項不是原本就是執行緒安全。 多執行緒可以公開您的程式碼非常嚴重且複雜的錯誤。 管理控制項的兩個或多個執行緒可以強制控制項進入不一致的狀態，並會導致競爭情況、 死結和凍結或停止回應。 如果您實作多執行緒在您的應用程式，務必以安全執行緒方式呼叫跨執行緒的控制項。 如需詳細資訊，請參閱 < [Managed 執行緒最佳做法](../../../../docs/standard/threading/managed-threading-best-practices.md)。 

有兩種方式可安全地從未建立該控制項的執行緒中呼叫的 Windows Form 控制項。 您可以使用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法來呼叫在主執行緒，也就會呼叫控制項中建立的委派。 或者，您可以實作<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>，這會使用事件驅動的模型來分隔結果報告在背景執行緒完成工作。 

## <a name="unsafe-cross-thread-calls"></a>不安全的跨執行緒呼叫

它並不安全呼叫控制項，直接從未建立的執行緒。 下列程式碼片段會示範不安全的對<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>控制項。 `Button1_Click`事件處理常式建立新`WriteTextUnsafe`設定的主執行緒的執行緒<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接屬性。 

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

Visual Studio 偵錯工具偵測到這些不安全的執行緒呼叫，藉由引發<xref:System.InvalidOperationException>訊息：**跨執行緒作業無效。控制 「 」 從其所建立的執行緒以外的執行緒存取。** <xref:System.InvalidOperationException>永遠不安全的跨執行緒呼叫 Visual Studio 偵錯時，就會發生，而且可能會發生在應用程式執行階段。 您應該修正問題，但您可以設定連線，停用例外狀況<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>屬性設`false`。

## <a name="safe-cross-thread-calls"></a>安全的跨執行緒呼叫 

下列程式碼範例示範兩種方式可安全地從未建立的執行緒中呼叫的 Windows Form 控制項： 
1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法，從主執行緒呼叫控制項呼叫委派。 
2. A<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，可提供的事件驅動模型。 

在這兩個範例中，以模擬一秒背景執行緒會休眠工作在該執行緒中完成。 

您可以建置並執行這些範例做為.NET Framework 應用程式，從C#或 Visual Basic 命令列。 如需詳細資訊，請參閱 <<c0> [ 使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或是[從命令列 (Visual Basic) 建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。 

從.NET Core 3.0 開始，您可以也建立並執行範例當做 Windows.NET Core 應用程式從資料夾具有.NET Core 的 Windows Forms *\<資料夾名稱 >.csproj*專案檔。 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>範例：使用委派的叫用方法

下列範例示範以確保安全執行緒呼叫至 Windows Form 控制項的模式。 它會查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>屬性，它會比較控制項的建立執行緒 ID，以呼叫的執行緒 id。 如果執行緒識別碼都相同，則會呼叫控制項直接。 如果執行緒識別碼不同，它會呼叫<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>從主執行緒，讓控制項實際呼叫的委派的方法。

`SafeCallDelegate`可讓設定<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。 `WriteTextSafe`方法查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A>。 如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>會傳回`true`，`WriteTextSafe`傳遞`SafeCallDelegate`到<xref:System.Windows.Forms.Control.Invoke%2A>進行控制項實際呼叫的方法。 如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>會傳回`false`，`WriteTextSafe`設定<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接。 `Button1_Click`事件處理常式會建立新的執行緒，並執行`WriteTextSafe`方法。 

 [!code-csharp[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>範例：使用 BackgroundWorker 事件處理常式

輕鬆地實作多執行緒是使用<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，可使用事件驅動的模型。 背景執行緒會執行<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>事件，不會與主執行緒互動。 主要執行緒會執行<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>事件處理常式，可以呼叫主執行緒的控制項。

若要使用時，進行安全執行緒呼叫<xref:System.ComponentModel.BackgroundWorker>、 在背景執行緒執行工作，建立一個方法，並繫結至<xref:System.ComponentModel.BackgroundWorker.DoWork>事件。 在主執行緒報告的背景工作，結果中建立另一個方法，並繫結至<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>或<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。 若要啟動背景執行緒，請呼叫<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>。 

此範例會使用<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>若要設定的事件處理常式<xref:System.Windows.Forms.TextBox>控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。 使用範例<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件，請參閱<xref:System.ComponentModel.BackgroundWorker>。 

 [!code-csharp[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.BackgroundWorker>
- [如何：在背景執行作業](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [如何：實作使用背景作業的表單](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [開發以.NET Framework 的自訂 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
