---
title: HOW TO：變更 Windows Forms 中 ToolStrip 文字和影像的外觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
ms.openlocfilehash: cf2f332b17bf6ff5b6ffb7cbc2d5777649728ec6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650849"
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="2a7ca-102">HOW TO：變更 Windows Forms 中 ToolStrip 文字和影像的外觀</span><span class="sxs-lookup"><span data-stu-id="2a7ca-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="2a7ca-103">您可以控制文字和影像會顯示在<xref:System.Windows.Forms.ToolStripItem>並與彼此相對的對齊方式和<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="2a7ca-104">若要定義 toolstripitem 所顯示的內容</span><span class="sxs-lookup"><span data-stu-id="2a7ca-104">To define what is displayed on a ToolStripItem</span></span>  
  
- <span data-ttu-id="2a7ca-105">設定<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="2a7ca-106">您可以徹底`Image`， `ImageAndText`， `None`，和`Text`。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="2a7ca-107">預設為 `ImageAndText`。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="2a7ca-108">若要對齊文字 toolstripitem</span><span class="sxs-lookup"><span data-stu-id="2a7ca-108">To align text on a ToolStripItem</span></span>  
  
- <span data-ttu-id="2a7ca-109">設定<xref:System.Windows.Forms.ToolStripItem.TextAlign%2A>屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="2a7ca-110">可能性有上方、 中間與下方左、 置中與權限的任何組合。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="2a7ca-111">預設為 `MiddleCenter`。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="2a7ca-112">若要對齊 toolstripitem 映像</span><span class="sxs-lookup"><span data-stu-id="2a7ca-112">To align an image on a ToolStripItem</span></span>  
  
- <span data-ttu-id="2a7ca-113">設定<xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="2a7ca-114">可能性有上方、 中間與下方左、 置中與權限的任何組合。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="2a7ca-115">預設為 `MiddleLeft`。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="2a7ca-116">若要定義 prvku ToolStripItem 文字和影像相對於其他的顯示方式</span><span class="sxs-lookup"><span data-stu-id="2a7ca-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
- <span data-ttu-id="2a7ca-117">設定<xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>屬性設為所需的值。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="2a7ca-118">您可以徹底`ImageAboveText`， `ImageBeforeText`， `Overlay`， `TextAboveImage`，和`TextBeforeImage`。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="2a7ca-119">預設為 `ImageBeforeText`。</span><span class="sxs-lookup"><span data-stu-id="2a7ca-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2a7ca-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a7ca-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="2a7ca-121">ToolStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="2a7ca-121">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="2a7ca-122">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="2a7ca-122">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="2a7ca-123">ToolStrip 技術摘要</span><span class="sxs-lookup"><span data-stu-id="2a7ca-123">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
