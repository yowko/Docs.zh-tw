---
title: 作法：從命令列建立 Windows Forms 應用程式
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72195dd49c163b26a5bcfa739768718f2a32f346
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588973"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>HOW TO：從命令列建立 Windows Forms 應用程式
下列程序說明若要從命令列建立及執行 Windows Forms 應用程式，所必須完成的基本步驟。 在 Visual Studio 中，對這些程序有廣泛的支援。  另請參閱[逐步解說：在 WPF 中裝載 Windows Forms 控制項](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-create-the-form"></a>建立表單  
  
1. 在空的程式碼檔案中，輸入下列匯入或使用陳述式：  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. 宣告繼承自表單類別且名為 `Form1` 的類別。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. 建立 `Form1` 的預設建構函式。  
  
     您在後續的程序中，會將更多程式碼加入建構函式中。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. 將 `Main` 方法加入類別中。  
  
    1. 適用於<xref:System.STAThreadAttribute>C#`Main`方法，以指定 Windows Forms 應用程式是單一執行緒的 apartment。 （屬性不需要在 Visual Basic 中，因為 Windows forms 應用程式開發與 Visual Basic 使用單一執行緒 apartment 模型的預設值。）  
  
    2. 呼叫<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>若要將作業系統樣式套用至您的應用程式。  
  
    3. 建立表單的執行個體，並加以執行。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>編譯和執行應用程式  
  
1. 在 .NET Framework 命令提示字元中，巡覽至您建立 `Form1` 類別的目錄。  
  
2. 編譯表單。  
  
    - 如果您使用的 C# 中，類型： `csc form1.cs`  
  
         `-or-`  
  
    - 如果您使用 Visual Basic 中，類型： `vbc form1.vb`  
  
3. 在命令提示字元中，輸入： `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>加入控制項和處理事件  
 先前的程序步驟示範只是如何建立可編譯和執行的基本 Windows Form。 下一個程序將會說明如何建立控制項並將其加入表單，以及處理控制項的事件。 如需您可以將它新增至 Windows Forms 控制項的相關資訊，請參閱 < [Windows Forms 控制項](./controls/index.md)。  
  
 除了了解如何建立 Windows Forms 應用程式，您還應該了解以事件為基礎的程式設計，以及如何處理使用者輸入。 如需詳細資訊，請參閱 <<c0> [ 在 Windows Forms 中建立事件處理常式](creating-event-handlers-in-windows-forms.md)，和[處理使用者輸入](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>宣告按鈕控制項及處理其 Click 事件  
  
1. 宣告名為 `button1` 的按鈕控制項。  
  
2. 在建構函式中，建立按鈕，並設定其 <xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A> 和 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
3. 將按鈕加入表單中。  
  
     下列程式碼範例會示範如何宣告按鈕控制項。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. 建立方法來處理按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
5. 在 Click 事件處理常式中，顯示含有 "Hello World" 訊息的 <xref:System.Windows.Forms.MessageBox>。  
  
     下列程式碼範例會示範如何處理按鈕控制項的 Click 事件。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. 使 <xref:System.Windows.Forms.Control.Click> 事件與您建立的方法產生關聯。  
  
     下列程式碼範例會示範如何將事件與方法產生關聯。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. 依照先前程序的說明，編譯及執行應用程式。  
  
## <a name="example"></a>範例  
 下列程式碼範例是先前程序的完整範例。  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [變更 Windows Forms 的外觀](changing-the-appearance-of-windows-forms.md)
- [增強 Windows Forms 應用程式](./advanced/index.md)
- [Windows Forms 使用者入門](getting-started-with-windows-forms.md)
