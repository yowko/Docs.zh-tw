---
title: 如何：為工具條控制項創建和設置自訂渲染器
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
ms.openlocfilehash: 49db0d785155f19b7220ac64011eaf4253aaa7e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182396"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>如何：建立和設定 Windows Form 中的 ToolStrip 控制項自訂產生器
<xref:System.Windows.Forms.ToolStrip>控制項為主題和樣式提供了簡單的支援。 通過將屬性或屬性設置為自訂呈現器，<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType><xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>可以完全自訂外觀和行為（外觀）。  
  
 <xref:System.Windows.Forms.ToolStrip>可以將渲染器分配給每個單獨的 、、<xref:System.Windows.Forms.ContextMenuStrip><xref:System.Windows.Forms.StatusStrip><xref:System.Windows.Forms.ToolStripManager.Renderer%2A><xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType><xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType><xref:System.Windows.Forms.MenuStrip>或控制項，也可以使用 屬性通過將 屬性設置為 來影響所有物件。  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>僅當<xref:System.Windows.Forms.ToolStripRenderMode.Custom>的值<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>不是`null`時才返回。  
  
### <a name="to-create-a-custom-renderer"></a>創建自訂渲染器  
  
1. 擴展類<xref:System.Windows.Forms.ToolStripRenderer>。  
  
2. 通過重寫適當的*On...* members  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>將自訂渲染器設置為當前渲染器  
  
1. 要為其中<xref:System.Windows.Forms.ToolStrip>設置自訂呈現器，將<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>屬性設置為自訂呈現器。  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. 或者為應用程式中包含的<xref:System.Windows.Forms.ToolStrip>所有類設置自訂呈現器：將<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>屬性設置為自訂呈現器，<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>並將該屬性設置為<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>。  
  
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
