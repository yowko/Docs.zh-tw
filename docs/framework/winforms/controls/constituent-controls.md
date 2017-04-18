---
title: "組成控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "組成控制項"
  - "自訂控制項 [Windows Form], 組成控制項"
  - "使用者控制項 [Windows Form], 組成控制項"
  - "UserControl 類別"
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 組成控制項
組成使用者控制項的控制項 \(或是所謂的*組成控制項*\) 在處理自訂圖形轉譯方面較不具彈性。  所有 Windows Form 控制項都是透過本身的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法處理本身的轉譯。  由於這個方法受到保護，所以開發人員無法存取它，也因此當繪製控制項時無法防止他人執行這個方法。  不過，這並不表示您不能加入程式碼來影響組成控制項的外觀。  您可加入事件處理常式來進行額外的轉譯。  例如，假設您要撰寫具有名為 `MyButton` 之按鈕的 <xref:System.Windows.Forms.UserControl>。  如果您要在 [Button 類別](frlrfSystemWebUIWebControlsButtonClassTopic)所提供的轉譯以外進行其他轉譯，您應將程式碼加入使用者控制項，如下所示：  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=   
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,   
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
>  有些 Windows Form 控制項 \(例如 <xref:System.Windows.Forms.TextBox>\) 是直接由 Windows 繪製的。  在這些執行個體中，絕不會呼叫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，因此也不會呼叫以上範例。  
  
 這會建立每次執行 `MyButton.Paint` 事件時都會執行的方法，藉此將額外圖形表示加入您的控制項中。  請注意，這並不能避免執行 `MyButton.OnPaint`，而且除了執行自訂繪製之外，仍會執行通常由按鈕所執行的所有繪製。  如需 GDI\+ 技術和自訂轉譯的詳細資訊，請參閱[使用 GDI\+ 建立圖形影像](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。  如果您要控制項有唯一的表示，最好是建立繼承控制項，並為其撰寫自訂轉譯程式碼。  如需詳細資訊，請參閱[使用者自訂描繪控制項](../../../../docs/framework/winforms/controls/user-drawn-controls.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.UserControl>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 [使用者自訂描繪控制項](../../../../docs/framework/winforms/controls/user-drawn-controls.md)   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)