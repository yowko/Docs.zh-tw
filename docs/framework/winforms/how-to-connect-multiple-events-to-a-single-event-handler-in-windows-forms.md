---
title: "如何：在 Windows Form 中連接多個事件至單一事件處理常式 | Microsoft Docs"
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
  - "事件處理常式 [Windows Form], 連接事件至"
  - "事件 [Windows Form], 將多個連接至單一事件處理常式"
  - "功能表項目, 多點傳送事件處理方法"
  - "功能表, 多個功能表項目的事件處理方法"
  - "Windows Form 控制項, 事件"
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：在 Windows Form 中連接多個事件至單一事件處理常式
設計應用程式時，您可能會發現多個事件必須使用同一個事件處理常式，或是多個事件會執行相同的程序。  例如，在所公開功能都相同的情況下，如果能讓功能表命令和表單上按鈕一樣引發相同事件的話，便可節省相當可觀的時間。  利用 C\# 中 \[屬性\] 視窗的 \[事件\] 檢視，或 Visual Basic 程式碼編輯器中的 `Handles`  關鍵字以及 \[**類別名稱**\] 和 \[**方法名稱**\] 下拉式方塊，都可以達到這項目的。  
  
### 若要在 Visual Basic 中將多個事件連接至同一個事件處理常式  
  
1.  在表單上按一下滑鼠右鍵，並選擇 \[**檢視程式碼**\]。  
  
2.  從 \[**類別名稱**\] 下拉式方塊中選取您指派給此事件處理常式處理的其中一個控制項。  
  
3.  從 \[**方法名稱**\] 下拉式方塊中選取您指派給此事件處理常式處理的其中一個事件。  
  
4.  程式碼編輯器會插入適當的事件處理常式並將插入點置入方法中。  在以下的範例中，即是 <xref:System.Windows.Forms.Button> 控制項的 <xref:System.Windows.Forms.Control.Click> 事件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  將其他您想要處理的事件附加至 `Handles`  子句。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  加入適當的程式碼至事件處理常式。  
  
### 若要在 C\# 中連接多個事件至單一事件處理常式  
  
1.  選取您要連接事件處理常式的控制項。  
  
2.  在 \[屬性\] 視窗中，按一下 \[**事件**\] 按鈕 ![事件符號](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton\_PropertiesWindow")。  
  
3.  按一下您要處理的事件名稱。  
  
4.  在事件名稱旁的值區段中按一下下拉式按鈕，接著會顯示現有事件處理常式的清單，這些處理常式與您要處理事件的方法簽章相符。  
  
5.  從清單中選取適當的事件處理常式。  
  
     程式碼將會加入表單，來將事件與現有的事件處理常式繫結起來。  
  
## 請參閱  
 [在 Windows Form 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [事件處理常式概觀](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)