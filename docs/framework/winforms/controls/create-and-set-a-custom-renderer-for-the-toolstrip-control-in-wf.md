---
title: HOW TO：建立和設定 Windows Forms 中 ToolStrip 控制項的自訂轉譯器
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
ms.openlocfilehash: ca1a7444c029632f83b1600e5855a13c83777594
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296377"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="559b1-102">HOW TO：建立和設定 Windows Forms 中 ToolStrip 控制項的自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="559b1-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="559b1-103"><xref:System.Windows.Forms.ToolStrip> 控制項讓您輕鬆支援佈景主題和樣式。</span><span class="sxs-lookup"><span data-stu-id="559b1-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="559b1-104">您可以達到完全自訂的外觀和行為 （外觀及操作） 設定<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>屬性或<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>自訂轉譯器的屬性。</span><span class="sxs-lookup"><span data-stu-id="559b1-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="559b1-105">您可以將轉譯器指派給每個個別<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>， <xref:System.Windows.Forms.ContextMenuStrip>，或<xref:System.Windows.Forms.StatusStrip>控制項，或者您可以使用<xref:System.Windows.Forms.ToolStripManager.Renderer%2A>屬性，以便藉由設定影響所有物件<xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType>屬性設<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="559b1-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="559b1-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 會傳回<xref:System.Windows.Forms.ToolStripRenderMode.Custom>只有當的值<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>不是`null`。</span><span class="sxs-lookup"><span data-stu-id="559b1-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="559b1-107">若要建立自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="559b1-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="559b1-108">擴充<xref:System.Windows.Forms.ToolStripRenderer>類別。</span><span class="sxs-lookup"><span data-stu-id="559b1-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="559b1-109">實作所需的自訂轉譯藉由覆寫適當*上...*</span><span class="sxs-lookup"><span data-stu-id="559b1-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="559b1-110">成員</span><span class="sxs-lookup"><span data-stu-id="559b1-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="559b1-111">若要設定為目前的轉譯器的自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="559b1-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="559b1-112">若要設定自訂轉譯器，其中<xref:System.Windows.Forms.ToolStrip>，將<xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType>自訂轉譯器的屬性。</span><span class="sxs-lookup"><span data-stu-id="559b1-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="559b1-113">或若要設定所有的自訂轉譯器<xref:System.Windows.Forms.ToolStrip>類別包含在您的應用程式：設定<xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>為自訂轉譯器並將屬性<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>屬性設<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>。</span><span class="sxs-lookup"><span data-stu-id="559b1-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="559b1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="559b1-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="559b1-115">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="559b1-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="559b1-116">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="559b1-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="559b1-117">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="559b1-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
