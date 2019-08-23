---
title: 作法：建立和設定 Windows Forms 中 ToolStrip 控制項的自訂轉譯器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929733"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>HOW TO：建立和設定 Windows Forms 中 ToolStrip 控制項的自訂轉譯器
<xref:System.Windows.Forms.ToolStrip>控制項可讓您輕鬆地支援主題和樣式。 您可以藉由將<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>屬性<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>或屬性設定為自訂轉譯器, 來達到完全自訂的外觀和行為 (外觀與風格)。  
  
 您可以將轉譯器指派給<xref:System.Windows.Forms.ToolStrip>每<xref:System.Windows.Forms.MenuStrip>個<xref:System.Windows.Forms.ContextMenuStrip>個別的<xref:System.Windows.Forms.StatusStrip> 、、 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>或控制項, 也<xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType>可以使用屬性來影響所有物件, 方法是將<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>屬性設定為。  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>只有在的<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>值不`null`是時, 才會傳回。 <xref:System.Windows.Forms.ToolStripRenderMode.Custom>  
  
### <a name="to-create-a-custom-renderer"></a>若要建立自訂轉譯器  
  
1. <xref:System.Windows.Forms.ToolStripRenderer>擴充類別。  
  
2. 藉由覆寫適當的來執行所需的自訂轉譯 *...* 成員  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>若要將自訂轉譯器設定為目前的轉譯器  
  
1. 若要設定其中一個<xref:System.Windows.Forms.ToolStrip>的自訂轉譯器, 請<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>將屬性設定為自訂轉譯器。  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. 或者, 若要為應用程式中<xref:System.Windows.Forms.ToolStrip>包含的所有類別設定自訂轉譯器:將屬性設定為自訂轉譯器, 並<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>將屬性設定為<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>。 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [ToolStrip 控制項概觀](toolstrip-control-overview-windows-forms.md)
- [ToolStrip 控制項架構](toolstrip-control-architecture.md)
- [ToolStrip 技術摘要](toolstrip-technology-summary.md)
