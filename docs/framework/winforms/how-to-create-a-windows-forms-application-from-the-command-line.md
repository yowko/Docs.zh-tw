---
title: "如何：從命令列建立 Windows Form 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Form, 從命令列開發應用程式"
  - "Windows Form, 建立基本表單"
  - "Windows Form, 使用者入門"
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：從命令列建立 Windows Form 應用程式
下列程序說明若要從命令列建立及執行 Windows Form 應用程式，所必須完成的基本步驟。  在 Visual Studio 中，對這些程序有廣泛的支援。  另請參閱[逐步解說：建立簡單的 Windows Form](http://msdn.microsoft.com/library/z9w2f38k%20\(v=vs.110\))。  
  
## 程序  
  
#### 建立表單  
  
1.  在空的程式碼檔案中，輸入下列匯入或使用陳述式：  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  宣告繼承自表單類別且名為 `Form1` 的類別。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  建立 `Form1` 的預設建構函式。  
  
     您在後續的程序中，會將更多程式碼加入建構函式中。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  將 `Main` 方法加入類別中。  
  
    1.  將 <xref:System.STAThreadAttribute> 套用至 `Main` 方法，以指定您的 Windows Form 應用程式是單一執行緒的 Apartment。  
  
    2.  呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>，為您的應用程式提供 Windows XP 外觀。  
  
    3.  建立表單的執行個體，並加以執行。  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### 編譯和執行應用程式  
  
1.  在 .NET Framework 命令提示字元中，巡覽至您建立 `Form1` 類別的目錄。  
  
2.  編譯表單。  
  
    -   如果您是使用 C\#，請輸入：`csc form1.cs`  
  
         `-或-`  
  
    -   如果您是使用 Visual Basic，請輸入：`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`  
  
3.  在命令提示字元中，輸入：`Form1.exe`  
  
## 加入控制項和處理事件  
 先前的程序步驟示範只是如何建立可編譯和執行的基本 Windows Form。  下一個程序將會說明如何建立控制項並將其加入表單，以及處理控制項的事件。  如需您可以加入 Windows Form 之控制項的相關資訊，請參閱 [Windows Form 控制項](../../../docs/framework/winforms/controls/index.md)。  
  
 除了了解如何建立 Windows Form 應用程式，您還應該了解以事件為基礎的程式設計，以及如何處理使用者輸入。  如需詳細資訊，請參閱[在 Windows Form 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)，以及[處理使用者輸入](../../../docs/framework/winforms/controls/handling-user-input.md)  
  
#### 宣告按鈕控制項及處理其 Click 事件  
  
1.  宣告名為 `button1` 的按鈕控制項。  
  
2.  在建構函式中，建立按鈕，並設定其 <xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A> 和 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
3.  將按鈕加入表單中。  
  
     下列程式碼範例會示範如何宣告按鈕控制項。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  建立方法來處理按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
5.  在 Click 事件處理常式中，顯示含有 "Hello World" 訊息的 <xref:System.Windows.Forms.MessageBox>。  
  
     下列程式碼範例會示範如何處理按鈕控制項的 Click 事件。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  使 <xref:System.Windows.Forms.Control.Click> 事件與您建立的方法產生關聯。  
  
     下列程式碼範例會示範如何將事件與方法產生關聯。  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  依照先前程序的說明，編譯及執行應用程式。  
  
## 範例  
 下列程式碼範例是先前程序的完整範例。  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## 編譯程式碼  
  
-   若要編譯程式碼，請遵循前面說明如何編譯及執行應用程式之程序中的指示。  
  
## 請參閱  
 <xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Control>   
 [變更 Windows Form 的外觀](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)   
 [增強 Windows Form 應用程式](../../../docs/framework/winforms/advanced/index.md)   
 [Windows Form 使用者入門](../../../docs/framework/winforms/getting-started-with-windows-forms.md)