---
title: 呈現 Windows Form 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- OnPaintBackground method [Windows Forms], invoking in Windows Forms custom controls
- custom controls [Windows Forms], graphics resources
- custom controls [Windows Forms], invalidation and painting
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
ms.openlocfilehash: a2d7a02e725e3f8065b80a6b30ea21158be43ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="rendering-a-windows-forms-control"></a>呈現 Windows Form 控制項
轉譯是指使用者的螢幕上建立的視覺表示法的程序。 Windows Form 使用[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]（新 Windows 圖形的程式庫） 來進行轉譯。 Managed 的類別，可提供存取權[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中<xref:System.Drawing?displayProperty=nameWithType>命名空間和及其子命名空間。  
  
 控制項的呈現涉及下列項目：  
  
-   基底類別所提供的繪圖功能<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。  
  
-   基本項目[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]圖形文件庫。  
  
-   繪圖區域的幾何。  
  
-   釋放圖形資源的程序。  
  
## <a name="drawing-functionality-provided-by-control"></a>繪製控制項所提供的功能  
 基底類別<xref:System.Windows.Forms.Control>提供繪圖功能透過其<xref:System.Windows.Forms.Control.Paint>事件。 控制項引發<xref:System.Windows.Forms.Control.Paint>每當必須更新其顯示的事件。 如需.NET Framework 中的事件的詳細資訊，請參閱[處理和引發事件](../../../../docs/standard/events/index.md)。  
  
 事件資料類別<xref:System.Windows.Forms.Control.Paint>事件， <xref:System.Windows.Forms.PaintEventArgs>，保存繪製控制項所需的資料 — 圖形物件，表示要繪製的區域的矩形物件的控制代碼。 中會顯示這些物件粗體顯示在下列程式碼片段。  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   Implements IDisposable  
  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property  
   ' Other properties and methods.  
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs, IDisposable {  
public System.Drawing.Rectangle ClipRectangle {get;}  
public System.Drawing.Graphics Graphics {get;}  
// Other properties and methods.  
...  
}  
```  
  
 <xref:System.Drawing.Graphics> 會封裝繪圖功能的 managed 的類別的討論內容中所述[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]本主題稍後。 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>的執行個體<xref:System.Drawing.Rectangle>結構，並定義控制項可以在其中繪製的可用區域。 控制項開發人員可以計算<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>使用<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>控制項，在本主題稍後的幾何的討論內容中所述的屬性。  
  
 控制項必須藉由覆寫提供轉譯邏輯<xref:System.Windows.Forms.Control.OnPaint%2A>它所繼承的方法<xref:System.Windows.Forms.Control>。 <xref:System.Windows.Forms.Control.OnPaint%2A> 取得圖形物件和要透過中繪製的矩形存取<xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A>和<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>傳遞給它的執行個體。  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>方法的基底<xref:System.Windows.Forms.Control>類別未實作任何繪圖功能，但只會叫用註冊的事件委派<xref:System.Windows.Forms.Control.Paint>事件。 當您覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>，您通常應該叫用<xref:System.Windows.Forms.Control.OnPaint%2A>方法的基底類別，使已註冊的委派能接收<xref:System.Windows.Forms.Control.Paint>事件。 不過，繪製其整個介面的控制項應該不會叫用基底類別的<xref:System.Windows.Forms.Control.OnPaint%2A>，如本主題將介紹閃爍。 如需覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>事件，請參閱[How to： 建立 Windows Form 控制項，顯示進度](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
> [!NOTE]
>  不會叫用<xref:System.Windows.Forms.Control.OnPaint%2A>直接從您的控制項; 相反地，叫用<xref:System.Windows.Forms.Control.Invalidate%2A>方法 (繼承自<xref:System.Windows.Forms.Control>) 或透過其他方法會叫用<xref:System.Windows.Forms.Control.Invalidate%2A>。 <xref:System.Windows.Forms.Control.Invalidate%2A>方法接著會叫用<xref:System.Windows.Forms.Control.OnPaint%2A>。 <xref:System.Windows.Forms.Control.Invalidate%2A>多載方法，並根據引數提供給<xref:System.Windows.Forms.Control.Invalidate%2A> `e`，部分或所有其螢幕區域，會重新繪製控制項。  
  
 基底<xref:System.Windows.Forms.Control>類別會定義可用於繪圖的另一種方法：<xref:System.Windows.Forms.Control.OnPaintBackground%2A>方法。  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 繪製背景 (因而圖形) 視窗的而且保證時，快速<xref:System.Windows.Forms.Control.OnPaint%2A>繪製詳細資料，可能是較慢，因為個別的繪製要求會結合成一個<xref:System.Windows.Forms.Control.Paint>事件，它涵蓋了所有需要的區域重新繪製。 您可能想要叫用<xref:System.Windows.Forms.Control.OnPaintBackground%2A>，比方說，您是否要繪製控制項的漸層色彩背景。  
  
 雖然<xref:System.Windows.Forms.Control.OnPaintBackground%2A>具有類似事件的術語表，而且會使用相同的引數為`OnPaint`方法，<xref:System.Windows.Forms.Control.OnPaintBackground%2A>不是真正的事件方法。 沒有任何`PaintBackground`事件和<xref:System.Windows.Forms.Control.OnPaintBackground%2A>不叫用事件委派。 在覆寫<xref:System.Windows.Forms.Control.OnPaintBackground%2A>方法，在衍生的類別並不需要叫用<xref:System.Windows.Forms.Control.OnPaintBackground%2A>其基底類別的方法。  
  
## <a name="gdi-basics"></a>GDI + 基本概念  
 <xref:System.Drawing.Graphics>類別提供方法來繪製圓形、 三角形、 弧線和省略符號，例如各種圖形，以及顯示文字的方法。 <xref:System.Drawing?displayProperty=nameWithType>命名空間和及其子命名空間包含類別，將封裝的圖形項目，例如圖形 （圓形、 矩形、 弧線和其他項目）、 色彩、 字型、 筆刷等等。 如需有關[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]，請參閱[使用 Managed 圖形類別](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)。 必要的[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]中也說明了[How to： 建立 Windows Form 控制項，顯示進度](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
## <a name="geometry-of-the-drawing-region"></a>幾何的繪圖區域  
 <xref:System.Windows.Forms.Control.ClientRectangle%2A>控制項的屬性指定的矩形區域，可在使用者螢幕上的控制項時<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>指定實際繪製的區域。 (請記住，已完成，繪製<xref:System.Windows.Forms.Control.Paint>事件方法之<xref:System.Windows.Forms.PaintEventArgs>做為其引數的執行個體)。 控制項可能需要繪製只有部分可用的區域中，控制項的顯示變更的案例時一小部分。 控制項開發人員必須在這些情況下，計算實際的矩形中繪製，並傳遞要<xref:System.Windows.Forms.Control.Invalidate%2A>。 多載的版本<xref:System.Windows.Forms.Control.Invalidate%2A>採用<xref:System.Drawing.Rectangle>或<xref:System.Drawing.Region>做為引數使用該引數來產生<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性<xref:System.Windows.Forms.PaintEventArgs>。  
  
 下列程式碼片段示範如何`FlashTrackBar`自訂控制項計算要繪製的矩形區域。 `client`變數代表<xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>屬性。 如需完整範例，請參閱[How to： 建立 Windows Form 控制項，顯示進度](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## <a name="freeing-graphics-resources"></a>釋放圖形資源  
 圖形物件是相當費時，因為它們使用系統資源。 這類物件包含的執行個體<xref:System.Drawing.Graphics?displayProperty=nameWithType>類別的執行個體及<xref:System.Drawing.Brush?displayProperty=nameWithType>， <xref:System.Drawing.Pen?displayProperty=nameWithType>，和其他圖形 」 類別。 很重要，您需要它，並釋放它建立圖形資源只要您在使用完。 如果您建立類型可實作<xref:System.IDisposable>介面，請呼叫其<xref:System.IDisposable.Dispose%2A>方法完成時使用它以釋放資源。  
  
 下列程式碼片段示範如何`FlashTrackBar`建立自訂控制項，並釋放<xref:System.Drawing.Brush>資源。 完整的原始程式碼，請參閱[How to： 建立 Windows Form 控制項，顯示進度](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：建立顯示進度的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
