---
title: HOW TO：自訂繪製 ToolStrip 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 9b3d6b9391971d4c2d012345b96c2ed64d33a998
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311041"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>HOW TO：自訂繪製 ToolStrip 控制項
<xref:System.Windows.Forms.ToolStrip> 控制項具有下列相關聯轉譯 (繪製) 類別的項目：  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> 提供的外觀和樣式，您的作業系統。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 提供的外觀和 Microsoft Office 樣式。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> 為其他兩個呈現類別的抽象基底類別。  
  
 若要對 <xref:System.Windows.Forms.ToolStrip> 自訂繪圖 (也稱為主控描繪)，您可以覆寫其中一個轉譯器類別，並變更轉譯邏輯的層面。  
  
 下列程序會說明自訂繪圖的各種層面。  
  
### <a name="to-switch-between-the-provided-renderers"></a>在提供的轉譯器之間切換  
  
-   將 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 屬性設定為所要的 <xref:System.Windows.Forms.ToolStripRenderMode> 值。  
  
     藉由 <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>，靜態 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 決定您應用程式的轉譯器。 <xref:System.Windows.Forms.ToolStripRenderMode> 的其他值為 <xref:System.Windows.Forms.ToolStripRenderMode.Custom>、<xref:System.Windows.Forms.ToolStripRenderMode.Professional> 和 <xref:System.Windows.Forms.ToolStripRenderMode.System>。  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>變更 Microsoft Office 樣式框線為直線  
  
-   請覆寫 <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>，但不要呼叫基底類別。  
  
> [!NOTE]
>  該方法有用於 <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripSystemRenderer> 和 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 的版本。  
  
### <a name="to-change-the-professionalcolortable"></a>變更 ProfessionalColorTable  
  
-   覆寫 <xref:System.Windows.Forms.ProfessionalColorTable> 和變更您想要的色彩。  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>變更您應用程式中的所有 ToolStrip 控制項轉譯  
  
1. 使用 <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> 屬性來選擇提供的轉譯器之其中一種。  
  
2. 使用 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> 來指派自訂轉譯器。  
  
3. 確保 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> 設定為 <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> 的預設值。  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>關閉整個應用程式的 Microsoft Office 色彩  
  
-   請設定 <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> 為 `false`。  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>關閉 ToolStrip 控制項的 Microsoft Office 色彩  
  
-   使用與下列程式碼範例類似的程式碼。  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [使用內建主控描繪支援的控制項](controls-with-built-in-owner-drawing-support.md)
- [HOW TO：建立和設定 Windows Forms 中 ToolStrip 控制項的自訂轉譯器](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
