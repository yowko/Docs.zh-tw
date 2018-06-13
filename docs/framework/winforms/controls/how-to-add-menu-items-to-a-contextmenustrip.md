---
title: 如何：將功能表項目加入至 ContextMenuStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: d044cf92cf7ce6db3425aacf397d6c7b4f111324
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524621"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="58761-102">如何：將功能表項目加入至 ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="58761-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="58761-103">您可以一次新增一個功能表項目或數個項目<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="58761-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="58761-104">若要將單一功能表項目加入 ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="58761-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="58761-105">使用<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法，將一個功能表項目<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="58761-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="58761-106">若要將數個功能表項目加入 ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="58761-106">To add several menu items to a ContextMenuStrip</span></span>  
  
-   <span data-ttu-id="58761-107">使用<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>方法，以將數個功能表項目加入<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="58761-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="58761-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58761-108">See Also</span></span>  
 [<span data-ttu-id="58761-109">ContextMenuStrip 控制項</span><span class="sxs-lookup"><span data-stu-id="58761-109">ContextMenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
