---
title: 如何：建立和設定 ToolStrip 控制項的自訂轉譯器
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
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743417"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="bc992-102">如何：建立和設定 Windows Form 中的 ToolStrip 控制項自訂產生器</span><span class="sxs-lookup"><span data-stu-id="bc992-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="bc992-103"><xref:System.Windows.Forms.ToolStrip> 控制項可讓您輕鬆地支援主題和樣式。</span><span class="sxs-lookup"><span data-stu-id="bc992-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="bc992-104">您可以藉由將 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> 屬性或 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> 屬性設定為自訂轉譯器，來達到完全自訂的外觀和行為（外觀及操作）。</span><span class="sxs-lookup"><span data-stu-id="bc992-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="bc992-105">您可以將轉譯器指派給每個個別的 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ContextMenuStrip>或 <xref:System.Windows.Forms.StatusStrip> 控制項，也可以使用 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> 屬性來影響所有物件，方法是將 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> 屬性設定為 [<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>]。</span><span class="sxs-lookup"><span data-stu-id="bc992-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc992-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 只有在 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> 的值不 `null`時，才會傳回 <xref:System.Windows.Forms.ToolStripRenderMode.Custom>。</span><span class="sxs-lookup"><span data-stu-id="bc992-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="bc992-107">若要建立自訂轉譯器</span><span class="sxs-lookup"><span data-stu-id="bc992-107">To create a custom renderer</span></span>  
  
1. <span data-ttu-id="bc992-108">擴充 <xref:System.Windows.Forms.ToolStripRenderer> 類別。</span><span class="sxs-lookup"><span data-stu-id="bc992-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2. <span data-ttu-id="bc992-109">藉由覆寫適當的來執行所需的自訂轉譯 *...*</span><span class="sxs-lookup"><span data-stu-id="bc992-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="bc992-110">成員</span><span class="sxs-lookup"><span data-stu-id="bc992-110">members</span></span>  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="bc992-111">若要將自訂轉譯器設定為目前的轉譯器</span><span class="sxs-lookup"><span data-stu-id="bc992-111">To set the custom renderer to be the current renderer</span></span>  
  
1. <span data-ttu-id="bc992-112">若要設定一個 <xref:System.Windows.Forms.ToolStrip>的自訂轉譯器，請將 <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> 屬性設定為自訂轉譯器。</span><span class="sxs-lookup"><span data-stu-id="bc992-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. <span data-ttu-id="bc992-113">或者，若要為應用程式中包含的所有 <xref:System.Windows.Forms.ToolStrip> 類別設定自訂轉譯器：將 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> 屬性設定為自訂轉譯器，並將 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 屬性設定為 [<xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>]。</span><span class="sxs-lookup"><span data-stu-id="bc992-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bc992-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="bc992-114">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [<span data-ttu-id="bc992-115">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="bc992-115">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="bc992-116">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="bc992-116">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="bc992-117">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="bc992-117">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
