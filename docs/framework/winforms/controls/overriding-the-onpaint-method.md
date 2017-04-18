---
title: "覆寫 OnPaint 方法 | Microsoft Docs"
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
  - "OnPaint 方法, 在 Windows Form 自訂控制項中覆寫"
  - "Paint 事件, 在 Windows Form 自訂控制項中處理"
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 覆寫 OnPaint 方法
覆寫定義在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 中任何事件的基本步驟是相同的，並且摘要在下列清單中。  
  
#### 若要覆寫繼承的事件  
  
1.  覆寫受保護的 `On`*EventName* 方法。  
  
2.  從覆寫的 `On`*EventName* 方法呼叫基底類別的 `On`*EventName* 方法，以便註冊的委派 \(Delegate\) 能接收事件。  
  
 <xref:System.Windows.Forms.Control.Paint> 事件將在這裡詳細討論，因為每一個 Windows Form 控制項都必須覆寫繼承自 <xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.Paint> 事件。  <xref:System.Windows.Forms.Control> 基底類別並不知如何繪製衍生控制項，而且不提供 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法中的任何繪製邏輯。  <xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法僅將 <xref:System.Windows.Forms.Control.Paint> 事件分派給已登錄的事件接收者。  
  
 若您是透過 [如何：開發簡單的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)中的範例來執行，則您已見過覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法的範例。  下列程式碼片段取自該範例。  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class   
```  
  
```csharp  
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs> 類別包含 <xref:System.Windows.Forms.Control.Paint> 事件的資料。  它具有兩個屬性，如下列程式碼所示。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property   
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 是要繪製的方框，且 <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> 屬性是參考至 <xref:System.Drawing.Graphics> 物件。  <xref:System.Drawing?displayProperty=fullName> 命名空間中的類別為 Managed 類別，提供對 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] \(新的 Windows 圖庫\) 功能的存取。  <xref:System.Drawing.Graphics> 物件具有方法，可繪製點、字串、直線、弧形、橢圓形和許多其他形狀。  
  
 每當控制項需要變更其視覺顯示時，會叫用其 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  這個方法會接著引發 <xref:System.Windows.Forms.Control.Paint> 事件。  
  
## 請參閱  
 [事件](../../../../docs/standard/events/index.md)   
 [呈現 Windows Form 控制項](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)   
 [定義事件](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)