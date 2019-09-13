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
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>作法：對 Windows Forms 控制項進行安全線程呼叫

多執行緒可以改善 Windows Forms 應用程式的效能，但 Windows Forms 控制項的存取原本就不是安全線程。 多執行緒可以將您的程式碼公開給非常嚴重且複雜的 bug。 操控控制項的兩個或多個執行緒可以強制控制項進入不一致的狀態，並導致競爭情況、鎖死、凍結或停止回應。 如果您在應用程式中執行多執行緒處理，請務必以執行緒安全的方式呼叫跨執行緒控制項。 如需詳細資訊，請參閱[Managed 執行緒最佳做法](../../../standard/threading/managed-threading-best-practices.md)。 

有兩種方式可以從未建立該控制項的執行緒安全地呼叫 Windows Forms 控制項。 您可以使用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法來呼叫在主執行緒中建立的委派，然後再呼叫該控制項。 或者，您可以執行<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>，它會使用事件驅動模型來分隔背景執行緒中完成的工作，使其無法報告結果。 

## <a name="unsafe-cross-thread-calls"></a>不安全的跨執行緒呼叫

不安全的方式是直接從未建立的執行緒呼叫控制項。 下列程式碼片段說明對<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>控制項的不安全呼叫。 事件處理常式會建立新`WriteTextUnsafe`的執行緒，它會直接設定主<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>執行緒的屬性。 `Button1_Click` 

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

Visual Studio 偵錯工具會藉由引發<xref:System.InvalidOperationException>與訊息， **跨執行緒作業無效來偵測這些不安全的執行緒呼叫。控制項 "" 是從建立它的執行緒以外的執行緒存取。** 在<xref:System.InvalidOperationException> Visual Studio 的調試期間，一律會發生不安全的跨執行緒呼叫，而且可能會在應用程式執行時間發生。 您應該修正此問題，但您可以藉由將<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>屬性設定為來`false`停用例外狀況。

## <a name="safe-cross-thread-calls"></a>安全的跨執行緒呼叫 

下列程式碼範例示範兩種安全地從未建立的執行緒呼叫 Windows Forms 控制項的方式： 

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>方法，它會從主執行緒呼叫委派以呼叫控制項。 
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，提供事件驅動模型。 

在這兩個範例中，背景執行緒會進入睡眠狀態一秒，以模擬在該執行緒中完成的工作。 

您可以從C#或 Visual Basic 命令列，將這些範例建立並執行為 .NET Framework 應用程式。 如需詳細資訊，請參閱[使用 ngen.exe 建立命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建立（Visual Basic）](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。 

從 .net core 3.0 開始，您也可以從具有 .net core Windows Forms  *\<資料夾名稱 > .csproj*專案檔的資料夾中，建立並執行範例做為 Windows .net core 應用程式。 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>範例：搭配使用 Invoke 方法與委派

下列範例示範的模式可確保對 Windows Forms 控制項的安全線程呼叫。 它會查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>屬性，其會將控制項的建立執行緒識別碼與呼叫執行緒識別碼進行比較。 如果執行緒識別碼相同，它會直接呼叫控制項。 如果執行緒識別碼不同，則會使用主執行緒<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>的委派來呼叫方法，這會對控制項進行實際的呼叫。

可讓您<xref:System.Windows.Forms.TextBox>設定控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。 `SafeCallDelegate` `WriteTextSafe`方法查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A>。 <xref:System.Windows.Forms.Control.InvokeRequired%2A> `SafeCallDelegate` 如果傳回<xref:System.Windows.Forms.Control.Invoke%2A> ，則`WriteTextSafe`會將傳遞至方法，以對控制項進行實際的呼叫。 `true` 如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>傳回 ，`WriteTextSafe`則會<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接設定。 `false` 事件處理常式會建立新的執行緒，並`WriteTextSafe`執行方法。 `Button1_Click` 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>範例：使用 BackgroundWorker 事件處理常式

執行多執行緒的簡單方法是<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>使用元件，其使用事件驅動模型。 背景執行緒會執行<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>事件，這不會與主執行緒互動。 主要執行緒會執行<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>和<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>事件處理常式，以呼叫主執行緒的控制項。

若要使用<xref:System.ComponentModel.BackgroundWorker>進行安全線程呼叫，請在背景執行緒中建立方法來執行工作，並將它系結<xref:System.ComponentModel.BackgroundWorker.DoWork>至事件。 在主執行緒中建立另一個方法，以報告背景工作的結果，並將它系結<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>至<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>或事件。 若要啟動背景執行緒，請<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>呼叫。 

這個範例會使用<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式來<xref:System.Windows.Forms.TextBox>設定控制項的<xref:System.Windows.Forms.TextBox.Text%2A>屬性。 如需使用<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>事件的範例，請<xref:System.ComponentModel.BackgroundWorker>參閱。 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.BackgroundWorker>
- [如何：在背景中執行作業](how-to-run-an-operation-in-the-background.md)
- [如何：執行使用背景作業的表單](how-to-implement-a-form-that-uses-a-background-operation.md)
- [使用 .NET Framework 開發自訂 Windows Forms 控制項](developing-custom-windows-forms-controls.md)
