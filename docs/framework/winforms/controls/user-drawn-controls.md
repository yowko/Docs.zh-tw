---
title: "使用者自訂描繪控制項 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 使用者繪製"
  - "OnPaint 方法 [Windows Form]"
  - "使用者自訂描繪控制項 [Windows Form]"
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 使用者自訂描繪控制項
.NET Framework 提供可讓您輕易開發您自己控制項的能力。  您可建立使用者控制項，即為由程式碼繫結在一起的一組標準控制項，或可重頭開始設計您自己的控制項。  您甚至可以使用繼承 \(Inheritance\) 來建立繼承自現有控制項的控制項，並且加入其繼承的功能。  無論使用的方法為何，.NET Framework 都提供功能來讓您為所建立的任何控制項繪製自訂圖形介面。  
  
 控制項的繪製是藉由執行控制項之 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法中的程式碼來達成。  <xref:System.Windows.Forms.Control.OnPaint%2A> 方法的單一引數是 <xref:System.Windows.Forms.PaintEventArgs> 物件，這個物件提供轉譯控制項所需的所有資訊和功能。  <xref:System.Windows.Forms.PaintEventArgs> 提供兩個做為屬性的主要物件，這些物件將用來轉譯您的控制項：  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 物件 \- 可繪製代表部分控制項的矩形。  根據繪製控制項的方法，決定這是整個控制項或是部分控制項。  
  
-   <xref:System.Drawing.Graphics> 物件 \- 封裝數個圖形導向的物件和方法，能夠提供繪製控制項所需的功能。  
  
 如需 <xref:System.Drawing.Graphics> 物件及其使用方式的詳細資訊，請參閱 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。  
  
 每當在螢幕上繪製或是重新整理控制項時，都會引發 <xref:System.Windows.Forms.Control.OnPaint%2A> 事件，而 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 物件代表了即將產生繪製的矩形。  如果整個控制項都需要重新整理，<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 將代表整個控制項的大小。  但是，如果只有部分控制項需要重新整理，<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 物件將僅代表需要重新繪製的區域。  例如，像是控制項因使用者介面中其他控制項或表單而變暗的情況。  
  
 當繼承 <xref:System.Windows.Forms.Control> 類別時，您必須覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法並在其中提供圖形轉譯程式碼。  如果您要將自訂圖形介面提供給使用者控制項或繼承的控制項，您也可以藉由覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法來這麼做。  如以下範例所示：  
  
```vb  
Protected Overrides Sub OnPaint(ByVal pe As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(pe)  
  
   ' Declare and instantiate a drawing pen.  
   Dim myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
  
   ' Draw an aqua rectangle in the rectangle represented by the control.  
   pe.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
End Sub  
  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs pe)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(pe);  
  
   // Declare and instantiate a new pen.  
   System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua);  
  
   // Draw an aqua rectangle in the rectangle represented by the control.  
   pe.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
      this.Size));  
}  
  
```  
  
 前例說明如何使用非常簡單的圖形表示來轉譯控制項。  因此會呼叫基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，建立用來繪製的 <xref:System.Drawing.Pen> 物件，最後在矩形中繪製由控制項 <xref:System.Windows.Forms.Control.Location%2A> 和 <xref:System.Windows.Forms.Control.Size%2A> 所決定的橢圓形。  雖然大部分的轉譯程式碼遠比這個範例複雜，不過這個範例仍說明了包含在 <xref:System.Drawing.Graphics> 物件中 <xref:System.Windows.Forms.PaintEventArgs> 物件的用法。  請注意，如果您繼承自已具有圖形表示的類別，例如 <xref:System.Windows.Forms.UserControl> 或 <xref:System.Windows.Forms.Button>，而且您不希望將這個表示加入轉譯，則不應呼叫基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法。  
  
 當第一次繪製控制項以及每當重新整理控制項的時侯，都將執行控制項的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法中的程式碼。  若要確保您的控制項在每次調整大小後都會重新繪製，請將下列這一行加入控制項的建構函式 \(Constructor\)：  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
  
```  
  
> [!NOTE]
>  使用 <xref:System.Windows.Forms.Control.Region%2A?displayProperty=fullName> 屬性來實作非矩形的控制項。  
  
## 請參閱  
 <xref:System.Windows.Forms.Control.Region%2A>   
 <xref:System.Windows.Forms.ControlStyles>   
 <xref:System.Drawing.Graphics>   
 <xref:System.Windows.Forms.Control.OnPaint%2A>   
 <xref:System.Windows.Forms.PaintEventArgs>   
 [如何：建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)   
 [組成控制項](../../../../docs/framework/winforms/controls/constituent-controls.md)   
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)