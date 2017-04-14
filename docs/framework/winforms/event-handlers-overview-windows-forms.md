---
title: "事件處理常式概觀 (Windows Form) | Microsoft Docs"
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
  - "事件處理常式, 關於事件處理常式"
  - "事件處理, Windows Form"
  - "Windows Form, 事件處理"
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 事件處理常式概觀 (Windows Form)
事件處理常式是繫結至事件的方法。  當事件引發時，會執行事件處理常式內的程式碼。  每個事件處理常式都提供兩個參數，可讓您適當處理事件。  以下範例顯示 <xref:System.Windows.Forms.Button> 控制項 <xref:System.Windows.Forms.Control.Click> 事件的事件處理常式。  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 第一個參數 `sender` 提供引發事件的物件參考。  上例中的第二個參數 `e` 傳遞的是針對欲處理事件的物件。  藉由參考物件的屬性 \(有時候是它的方法\)，您可以取得一些資訊，例如：mouse 事件的滑鼠位置，或是 drag\-and\-drop 事件中傳送的資料。  
  
 通常每個事件會產生與第二個參數的事件物件型別不同的事件處理常式。  某些事件處理常式，例如用於 <xref:System.Windows.Forms.Control.MouseDown> 和 <xref:System.Windows.Forms.Control.MouseUp> 事件的事件處理常式，則與第二個參數屬於相同的物件型別。  針對這些類型的事件，您可使用相同的事件處理常式來處理這兩種事件。  
  
 您也可以使用相同的事件處理常式來處理不同控制項的相同事件。  舉例來說，假設表單上有一群 <xref:System.Windows.Forms.RadioButton> 控制項，您就可以針對 <xref:System.Windows.Forms.Control.Click> 事件建立一個事件處理常式，然後將每一個控制項的 <xref:System.Windows.Forms.Control.Click> 事件繫結到這個事件處理常式。  如需詳細資訊，請參閱 [如何：在 Windows Form 中連接多個事件至單一事件處理常式](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)。  
  
## 請參閱  
 [在 Windows Form 中建立事件處理常式](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [事件概觀](../../../docs/framework/winforms/events-overview-windows-forms.md)