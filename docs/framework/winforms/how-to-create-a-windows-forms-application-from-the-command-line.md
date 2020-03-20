---
title: 從命令列創建 Windows 表單應用程式
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181992"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>如何：從命令列創建 Windows 表單應用程式

下列程序說明若要從命令列建立及執行 Windows Forms 應用程式，所必須完成的基本步驟。 在 Visual Studio 中，對這些程序有廣泛的支援。  另請參閱[演練：在 WPF 中託管 Windows 表單控制項](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)。
  
## <a name="procedure"></a>程序  
  
#### <a name="to-create-the-form"></a>建立表單  
  
1. 在空代碼檔中，鍵入以下`Imports`或`using`語句：  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. 聲明從 Form`Form1`類繼承的名為的類：
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. 為`Form1`創建 無參數建構函式。
  
     您在後續的程序中，會將更多程式碼加入建構函式中。
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. 將 `Main` 方法加入類別中。
  
    1. 將<xref:System.STAThreadAttribute>應用 到`Main`C# 方法以指定 Windows 表單應用程式是單線程單元。 （在 Visual Basic 中不需要該屬性，因為預設情況下，使用 Visual Basic 開發的 Windows 表單應用程式使用單線程單元模型。  
  
    2. 調用<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>以將作業系統樣式應用於應用程式。  
  
    3. 建立表單的執行個體，並加以執行。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>編譯和執行應用程式  
  
1. 在 .NET Framework 命令提示字元中，巡覽至您建立 `Form1` 類別的目錄。  
  
2. 編譯表單。  
  
    - 如果使用 C#，則鍵入：`csc form1.cs`  
  
         `-or-`  
  
    - 如果使用 Visual Basic，則鍵入：`vbc form1.vb`  
  
3. 在命令提示字元中，輸入：`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>添加控制項和處理事件

先前的程序步驟示範只是如何建立可編譯和執行的基本 Windows Form。 下一個程序將會說明如何建立控制項並將其加入表單，以及處理控制項的事件。 有關可添加到 Windows 表單的控制項的詳細資訊，請參閱[Windows 表單控制項](./controls/index.md)。
  
 除了了解如何建立 Windows Forms 應用程式，您還應該了解以事件為基礎的程式設計，以及如何處理使用者輸入。 有關詳細資訊，請參閱在[Windows 表單 中創建事件處理常式](creating-event-handlers-in-windows-forms.md)[和處理使用者輸入](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>宣告按鈕控制項及處理其 Click 事件  
  
1. 宣告名為 `button1` 的按鈕控制項。  
  
2. 在建構函式中，建立按鈕，並設定其 <xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A> 和 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
3. 將按鈕加入表單中。  
  
     以下代碼示例演示如何聲明按鈕控制項：
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. 建立方法來處理按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
5. 在 Click 事件處理常式中，顯示含有 "Hello World" 訊息的 <xref:System.Windows.Forms.MessageBox>。  
  
     以下代碼示例演示如何處理按鈕控制項的按一下事件：
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. 使 <xref:System.Windows.Forms.Control.Click> 事件與您建立的方法產生關聯。  
  
     下列程式碼範例會示範如何將事件與方法產生關聯。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. 依照先前程序的說明，編譯及執行應用程式。  
  
## <a name="example"></a>範例  

以下代碼示例是前面過程的完整示例：
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [變更 Windows Forms 的外觀](changing-the-appearance-of-windows-forms.md)
- [增強 Windows Forms 應用程式](./advanced/index.md)
- [Windows Forms 使用者入門](getting-started-with-windows-forms.md)
