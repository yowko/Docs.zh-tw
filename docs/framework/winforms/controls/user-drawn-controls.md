---
title: 使用者自訂描繪控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: 06513fc44782c78d2d69b82130542949519c0107
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158440"
---
# <a name="user-drawn-controls"></a>使用者自訂描繪控制項
.NET Framework 會提供您能夠輕鬆地開發自己的控制項。 您可以建立使用者控制項，也就是一組標準的控制項繫結在一起的程式碼，或您可以設計自己的控制項所打造的註冊。 您甚至可以使用繼承建立繼承自現有控制項的控制項，並將新增至其固有的功能。 任何方法使用時，.NET Framework 提供的功能，以繪製自訂的圖形化介面，以您所建立的任何控制項。  
  
 繪製控制項的作業透過在控制項的程式碼執行<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 單一引數<xref:System.Windows.Forms.Control.OnPaint%2A>方法是<xref:System.Windows.Forms.PaintEventArgs>物件，提供的所有資訊和呈現您的控制項時所需的功能。 <xref:System.Windows.Forms.PaintEventArgs>提供兩個主體物件，用以在呈現控制項的屬性：  
  
-   <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 物件的矩形，表示要繪製之控制項的部分。 這可以是整個控制項或根據控制項如何繪製控制項的一部分。  
  
-   <xref:System.Drawing.Graphics> 物件-封裝數個圖形導向物件和方法，可提供繪製控制項所需的功能。  
  
 如需詳細資訊<xref:System.Drawing.Graphics>物件，以及如何使用它，請參閱[How to:建立繪圖的圖形物件](../advanced/how-to-create-graphics-objects-for-drawing.md)。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>繪製或在畫面上，重新整理控制項時，會引發事件和<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件都代表在其中繪製，就會進行的矩形。 如果要重新整理，需要整個控制項<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>將代表整個控制項的大小。 如果只有部分控制項需要重新整理，不過，<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>物件將代表需要重新繪製的區域。 這種情況的範例就是當控制項已由另一個控制項或表單的使用者介面中此部分遮蔽。  
  
 當繼承自<xref:System.Windows.Forms.Control>類別，您必須覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，並提供中的圖形轉譯程式碼。 如果您想要提供自訂的圖形化介面，以使用者控制項或繼承的控制項，您也可以執行，藉由覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法。 範例如下所示：  
  
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
  
 上述範例示範如何呈現控制項的非常簡單的圖形表示法。 它會呼叫<xref:System.Windows.Forms.Control.OnPaint%2A>基底類別的方法，它會建立<xref:System.Drawing.Pen>物件用來繪製，而最後的橢圓形的矩形中繪製取決於<xref:System.Windows.Forms.Control.Location%2A>和<xref:System.Windows.Forms.Control.Size%2A>的控制項。 雖然大部分的轉譯程式碼會更加複雜一點，但此範例示範如何使用<xref:System.Drawing.Graphics>內含的物件<xref:System.Windows.Forms.PaintEventArgs>物件。 請注意，如果您繼承自的類別，已有的圖形表示法，例如<xref:System.Windows.Forms.UserControl>或是<xref:System.Windows.Forms.Button>，而且您不想將該表示併入您的轉譯，您不應該呼叫基底類別的<xref:System.Windows.Forms.Control.OnPaint%2A>方法。  
  
 中的程式碼<xref:System.Windows.Forms.Control.OnPaint%2A>第一次繪製控制項時，以及重新整理時，將會執行您的控制項的方法。 若要確保每次調整大小重新繪製控制項，請將下行新增至您的控制項的建構函式：  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  使用<xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType>來實作非矩形控制項的屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [HOW TO：建立繪製的圖形物件](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [組成控制項](constituent-controls.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
