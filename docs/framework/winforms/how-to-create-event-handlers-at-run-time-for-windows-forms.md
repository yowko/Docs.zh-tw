---
title: "如何：建立 Windows Form 的執行階段事件處理常式 | Microsoft Docs"
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
  - "Button 控制項 [Windows Form], 事件處理常式"
  - "事件處理常式, 建立"
  - "範例 [Windows Form], 事件處理"
  - "執行階段, 建立事件處理常式"
  - "Windows Form, 事件處理"
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 如何：建立 Windows Form 的執行階段事件處理常式
事件除了可以透過 Windows Form 設計工具建立之外，也可以在執行階段建立事件的處理常式。  這種方法可以讓您在執行階段根據程式碼中的條件，連接事件處理常式，不需要在程式一開始啟動時就進行連接。  
  
### 若要在執行階段建立事件處理常式  
  
1.  在程式碼編輯器中開啟想要加入事件處理常式的表單。  
  
2.  使用要處理事件的方法簽章，將方法加入表單中。  
  
     例如，如果您要處理 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件，則會建立如下的方法：  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  在事件處理常式中加入適用於應用程式的程式碼。  
  
4.  決定您要建立事件處理常式的表單或控制項。  
  
5.  在表單類別內的方法中，加入指定事件處理常式處理事件的程式碼。  例如以下程式碼便指定用 `button1_Click` 事件處理常式處理 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件：  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     上述 Visual Basic 程式碼中說明的 <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> 方法，會建立按鈕的 Click 事件處理常式。  
  
## 請參閱  
 [在 Windows Form 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [事件處理常式概觀](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)   
 [Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)