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
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>如何：對 Windows 表單控制項進行執行緒安全調用

多執行緒可以提高 Windows 表單應用的性能，但訪問 Windows 表單控制項本質上並不安全線程。 多執行緒可能會將代碼暴露給非常嚴重和複雜的錯誤。 操作控制項的兩個或多個執行緒可能會強制控制項進入不一致狀態，並導致競爭條件、鎖死以及凍結或掛起。 如果在應用中實現多執行緒讀取，請確保以執行緒安全的方式調用交叉執行緒控制項。 有關詳細資訊，請參閱[託管執行緒最佳實踐](../../../standard/threading/managed-threading-best-practices.md)。

有兩種方法可以從未創建該控制項的執行緒安全地調用 Windows 表單控制項。 可以使用 方法<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>調用在主執行緒中創建的委託，而主執行緒又調用控制項。 或者，可以實現 一<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>個 ，它使用事件驅動的模型將後臺執行緒中完成的工作與報告結果分開。

## <a name="unsafe-cross-thread-calls"></a>不安全的交叉執行緒調用

直接從未創建控制項的執行緒調用控制項是不安全的。 以下程式碼片段說明了對控制項的<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>不安全調用。 事件`Button1_Click`處理常式創建一個新`WriteTextUnsafe`執行緒，該執行緒直接設置主執行緒的屬性。 <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>

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

Visual Studio 調試器通過引發消息中的 調用<xref:System.InvalidOperationException>來檢測這些不安全的執行緒調用，**跨執行緒操作無效。控制項""從創建該執行緒以外的執行緒訪問。** 在<xref:System.InvalidOperationException>Visual Studio 調試期間，始終發生不安全的交叉執行緒調用，並且可能在應用運行時發生。 應修復此問題，但可以通過將<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>屬性設置為`false`來禁用異常。

## <a name="safe-cross-thread-calls"></a>安全交叉執行緒調用

以下代碼示例演示了從未創建該控制項的執行緒安全地調用 Windows 表單控制項的兩種方法：

1. 方法<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>，它從主執行緒調用委託來調用控制項。
2. 提供<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>事件驅動模型的元件。

在這兩個示例中，後臺執行緒休眠一秒鐘以類比該執行緒中正在完成的工作。

可以從 C# 或 Visual Basic 命令列生成和運行這些示例為 .NET 框架應用。 有關詳細資訊，請參閱使用[csc.exe 的命令列構建](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[命令列（可視基本）中的生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。

從 .NET Core 3.0 開始，您還可以從具有 .NET 核心 Windows 表單*\<資料夾名稱>.csproj*專案檔案的資料夾中生成並運行 Windows .NET Core 應用示例。

## <a name="example-use-the-invoke-method-with-a-delegate"></a>示例：使用具有委託的 Invoke 方法

下面的示例演示了用於確保對 Windows 表單控制項進行執行緒安全調用的模式。 它查詢該<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>屬性，該屬性將控制項的創建執行緒 ID 與調用執行緒 ID 進行比較。 如果執行緒指示相同，它將直接調用控制項。 如果執行緒指示不同，它將使用主執行緒的委託調用<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>方法，從而對控制項進行實際調用。

啟用`SafeCallDelegate`設置<xref:System.Windows.Forms.TextBox>控制項的屬性<xref:System.Windows.Forms.TextBox.Text%2A>。 方法`WriteTextSafe`查詢<xref:System.Windows.Forms.Control.InvokeRequired%2A>。 如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>返回`true` `WriteTextSafe` ，則`SafeCallDelegate`將<xref:System.Windows.Forms.Control.Invoke%2A>傳遞給 方法以對控制項進行實際調用。 如果<xref:System.Windows.Forms.Control.InvokeRequired%2A>返回`false` `WriteTextSafe` ，則<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接設置 。 事件`Button1_Click`處理常式創建新執行緒並運行方法`WriteTextSafe`。

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>示例：使用後臺輔助角色事件處理常式

實現多執行緒的一種簡單方法是使用<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>元件，該元件使用事件驅動的模型。 後臺執行緒運行事件<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>，該事件不與主執行緒交互。 主執行緒運行 和<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType><xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>事件處理常式，可以調用主執行緒的控制項。

要使用 進行<xref:System.ComponentModel.BackgroundWorker>執行緒安全調用，請在後臺執行緒中創建一個方法來執行該工作，並將其綁定到<xref:System.ComponentModel.BackgroundWorker.DoWork>事件。 在主執行緒中創建另一種方法以報告後臺工作的結果，並將其綁定到<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>或<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件。 要啟動後臺執行緒，請調用<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>。

該示例使用<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>事件處理常式設置<xref:System.Windows.Forms.TextBox>控制項的屬性。 <xref:System.Windows.Forms.TextBox.Text%2A> 有關使用事件的示例，<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>請參閱<xref:System.ComponentModel.BackgroundWorker>。

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>另請參閱

- <xref:System.ComponentModel.BackgroundWorker>
- [操作方式：在後臺運行操作](how-to-run-an-operation-in-the-background.md)
- [如何：實現使用後臺操作的表單](how-to-implement-a-form-that-uses-a-background-operation.md)
- [使用 .NET 框架開發自訂 Windows 表單控制項](developing-custom-windows-forms-controls.md)
