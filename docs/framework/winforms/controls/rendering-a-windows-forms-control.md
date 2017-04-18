---
title: "呈現 Windows Form 控制項 | Microsoft Docs"
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
  - "自訂控制項 [Windows Form], 圖形資源"
  - "自訂控制項 [Windows Form], 失效及繪製"
  - "自訂控制項 [Windows Form], 呈現"
  - "OnPaintBackground 方法, 在 Windows Form 自訂控制項中叫用"
ms.assetid: aae8e1e6-4786-432b-a15e-f4c44760d302
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 呈現 Windows Form 控制項
呈現意指在使用者螢幕上建立視覺表現的過程。  Windows Form 使用 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] \(新的 Windows 圖庫\) 來呈現。  提供對 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 存取的 Managed 類別是位於 <xref:System.Drawing?displayProperty=fullName> 命名空間和它的子命名空間。  
  
 下列項目涉及控制項的呈現。  
  
-   基底類別 <xref:System.Windows.Forms.Control?displayProperty=fullName> 所提供的繪圖功能。  
  
-   [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 圖庫的基本項目。  
  
-   繪圖區域的幾何形狀。  
  
-   釋放圖形資源的程序。  
  
## 控制項提供的繪圖功能  
 基底類別 <xref:System.Windows.Forms.Control> 透過其 <xref:System.Windows.Forms.Control.Paint> 事件來提供繪圖功能。  每當控制項需要更新其顯示時，就會引發 <xref:System.Windows.Forms.Control.Paint> 事件。  如需 .NET Framework 中事件的詳細資訊，請參閱[處理和引發事件](../../../../docs/standard/events/index.md)。  
  
 <xref:System.Windows.Forms.Control.Paint> 事件的事件資料類別 <xref:System.Windows.Forms.PaintEventArgs> 儲存繪製控制項所需的資料 — 圖形物件的控制代碼和代表要繪入的區域的矩形物件。  這些物件會以粗體顯示在下列程式碼片段中。  
  
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
  
 <xref:System.Drawing.Graphics> 為 Managed 類別，會封裝本主題稍後在 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 討論中說明的繪圖功能。  <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 是 <xref:System.Drawing.Rectangle> 結構的執行個體，並定義控制項能夠繪入的可用區域。  控制項開發人員可以使用控制項的 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性來計算 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>，如本主題稍後的幾何形狀討論中所說明的。  
  
 控制項必須藉由覆寫繼承自 <xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法來提供呈現邏輯。  <xref:System.Windows.Forms.Control.OnPaint%2A> 會透過傳遞至它的 <xref:System.Windows.Forms.PaintEventArgs> 執行個體的 <xref:System.Drawing.Design.PaintValueEventArgs.Graphics%2A> 和 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性，取得對要繪入之圖形物件和方框的存取。  
  
```vb  
Protected Overridable Sub OnPaint(pe As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaint(PaintEventArgs pe);  
```  
  
 基底 <xref:System.Windows.Forms.Control> 類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法不實作任何繪圖功能，而只是叫用 \(Invoke\) 使用 <xref:System.Windows.Forms.Control.Paint> 事件註冊的事件委派 \(Delegate\)。  當您覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 時，您基本上應該叫用基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，以便註冊的委派接收 <xref:System.Windows.Forms.Control.Paint> 事件。  然而，繪製整個平面的控制項不應該會叫用基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A>，因為這會造成閃動。  如需覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A> 事件的範例，請參閱 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
> [!NOTE]
>  不要直接從您的控制項叫用 <xref:System.Windows.Forms.Control.OnPaint%2A>；反而要叫用 <xref:System.Windows.Forms.Control.Invalidate%2A> 方法 \(繼承自 <xref:System.Windows.Forms.Control>\) 或某個叫用 <xref:System.Windows.Forms.Control.Invalidate%2A> 的其他方法。  <xref:System.Windows.Forms.Control.Invalidate%2A> 方法會接著叫用 <xref:System.Windows.Forms.Control.OnPaint%2A>。  <xref:System.Windows.Forms.Control.Invalidate%2A> 方法為多載，並且取決於供應給 <xref:System.Windows.Forms.Control.Invalidate%2A> `e` 的引數，控制項將重繪其螢幕區域的局部或全部。  
  
 基底 <xref:System.Windows.Forms.Control> 類別會定義另一個對繪圖有用處的方法 — <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 方法。  
  
```vb  
Protected Overridable Sub OnPaintBackground(pevent As PaintEventArgs)  
```  
  
```csharp  
protected virtual void OnPaintBackground(PaintEventArgs pevent);  
```  
  
 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 會繪製視窗的背景 \(和附帶的形狀\)，並保證速度很快；<xref:System.Windows.Forms.Control.OnPaint%2A> 則繪製細節，但可能很緩慢，因為個別的繪製要求會組合成一個 <xref:System.Windows.Forms.Control.Paint> 事件以覆蓋所有必須重繪的區域。  舉例來說，如果想為控制項繪製漸層色彩的背景，您可能會想要叫用 <xref:System.Windows.Forms.Control.OnPaintBackground%2A>。  
  
 雖然 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 具有類似事件的命名方式，而且接受和 `OnPaint` 方法相同的引數，但 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 並不是真正的事件方法。  沒有 `PaintBackground` 事件，而 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 也不叫用事件委派。  覆寫 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 方法時，衍生類別 \(Derived Class\) 不需要叫用其基底類別的 <xref:System.Windows.Forms.Control.OnPaintBackground%2A> 方法。  
  
## GDI\+ 基礎  
 <xref:System.Drawing.Graphics> 類別提供繪製各種圖形 \(例如圓形、三角形、弧形和橢圓形\) 的方法，以及顯示文字的方法。  <xref:System.Drawing?displayProperty=fullName> 命名空間和它的子命名空間包含有類別，可封裝圖形項目，例如形狀 \(例如圓形、三角形、弧形和其他\)、色彩、字型、筆刷等等。  如需 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 的詳細資訊，請參閱[使用 Managed 圖形類別](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)。  [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 的基本資訊在 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md) 中也有說明。  
  
## 繪圖區域的幾何學  
 控制項的 <xref:System.Windows.Forms.Control.ClientRectangle%2A> 屬性會指定使用者螢幕上控制項可用的矩形區域，而 <xref:System.Windows.Forms.PaintEventArgs> 的 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性則指定實際繪製的區域   \(請記住，繪製是在接受 <xref:System.Windows.Forms.PaintEventArgs> 執行個體做為其引數的 <xref:System.Windows.Forms.Control.Paint> 事件方法中完成\)。  控制項可能只需繪製其可用區域的一部分，正如在控制項的一小塊顯示變更時。  在那些場合，控制項開發人員必須計算實際要繪入的矩形，並將它傳遞給 <xref:System.Windows.Forms.Control.Invalidate%2A>。  接受 <xref:System.Drawing.Rectangle> 或 <xref:System.Drawing.Region> 做為引數的 <xref:System.Windows.Forms.Control.Invalidate%2A> 多載版本，會使用該引數來產生 <xref:System.Windows.Forms.PaintEventArgs> 的 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性。  
  
 下列程式碼範例片段示範 `FlashTrackBar` 自訂控制項如何計算要繪入的矩形區域。  `client` 變數代表 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> 屬性。  如需完整範例，請參閱 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#6)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#6)]  
  
## 釋放圖形資源  
 圖形物件很耗費資源，因為它們使用系統資源。  這些物件包括 <xref:System.Drawing.Graphics?displayProperty=fullName> 類別的執行個體、<xref:System.Drawing.Brush?displayProperty=fullName> 的執行個體、<xref:System.Drawing.Pen?displayProperty=fullName> 以及其他圖形類別。  您只有需要時才建立圖形資源，並且只要使用完畢即釋出，這是很重要的。  如果您建立實作 <xref:System.IDisposable> 介面的型別，請在完成時呼叫其 <xref:System.IDisposable.Dispose%2A> 方法，以便釋放資源。  
  
 下列程式碼片段示範 `FlashTrackBar` 自訂控制項如何建立並釋出 <xref:System.Drawing.Brush> 資源。  如需完整的原始程式碼，請參閱 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#5)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#5)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#4)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#4)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#3)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#3)]  
  
## 請參閱  
 [如何：建立顯示進度的 Windows Form 控制項](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)