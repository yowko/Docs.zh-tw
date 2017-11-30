---
title: "使用者自訂描繪控制項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42f208d10b1c111f98af3c803148590466baddf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="user-drawn-controls"></a>使用者自訂描繪控制項
.NET Framework 會提供您能夠輕鬆地開發您自己的控制項。 您可以建立使用者控制項，也就是一組標準的控制項繫結在一起的程式碼，或您可以設計自己的控制項，從頭組成。 您甚至可以使用繼承建立繼承自現有的控制項的控制項，並將新增到其繼承的功能。 方法使用時，.NET Framework 提供的功能，以繪製自訂的圖形化介面，任何您所建立的控制項。  
  
 繪製控制項的作業透過在控制項的程式碼執行<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 單一引數<xref:System.Windows.Forms.Control.OnPaint%2A>方法<xref:System.Windows.Forms.PaintEventArgs>物件，提供的所有資訊和轉譯控制項時所需的功能。 <xref:System.Windows.Forms.PaintEventArgs>做為屬性提供將用於程式控制項的呈現的兩個主要物件：  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件的矩形，表示要繪製之控制項的一部分。 這可以是整個控制項或根據如何繪製控制項的控制項的一部分。  
  
-   <xref:System.Drawing.Graphics>物件-封裝數個圖形導向的物件和方法，提供繪製控制項所需的功能。  
  
 如需有關<xref:System.Drawing.Graphics>物件，以及如何使用它，請參閱[How to： 建立繪製的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>繪製或重新整理在畫面上，控制項時引發事件和<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件都代表在其中繪製，就會進行的矩形。 如果需要重新整理整個控制項<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>將代表整個控制項的大小。 如果只有部分控制項需要重新整理，不過，<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件將代表需要重新繪製的區域。 這種情況的範例狀況是當控制項已部分遮蔽其他控制項或表單中的使用者介面。  
  
 繼承自<xref:System.Windows.Forms.Control>類別，您必須覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法並提供圖形轉譯程式碼中的。 如果您想要提供自訂的圖形化介面，以使用者控制項或繼承的控制項，您也可以執行，藉由覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 範例如下所示：  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,   
         this.Size));  
   }
}  
```  
  
 上述範例示範如何呈現控制項，以非常簡單的圖形表示法。 它會呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>基底類別的方法，它會建立<xref:System.Drawing.Pen>物件用來繪製，而最後的橢圓形的矩形中繪製取決於<xref:System.Windows.Forms.Control.Location%2A>和<xref:System.Windows.Forms.Control.Size%2A>的控制項。 雖然大部分的轉譯程式碼將會明顯比這更複雜，但是這個範例示範如何使用<xref:System.Drawing.Graphics>物件內含<xref:System.Windows.Forms.PaintEventArgs>物件。 請注意，如果您繼承自類別已有的圖形表示法，例如<xref:System.Windows.Forms.UserControl>或<xref:System.Windows.Forms.Button>，而且您不想要併入您呈現的表示法，您不應該呼叫基底類別的<xref:System.Windows.Forms.Control.OnPaint%2A>方法。  
  
 中的程式碼<xref:System.Windows.Forms.Control.OnPaint%2A>第一次繪製控制項時，以及重新整理時，將執行控制項的方法。 若要確保每次會調整大小重繪控制項，加入下列控制項的建構函式：  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  使用<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>實作非矩形控制項的屬性。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [操作說明：建立繪圖的圖形物件](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [組成控制項](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
