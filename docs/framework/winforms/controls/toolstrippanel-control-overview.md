---
title: "ToolStripPanel 控制項概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripPanel
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms], about ToolStripPanel control
ms.assetid: ce54a60c-5eba-4b4c-bd77-cf0748a666cc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bed2f4cbdc2f7d2e2647e39163959aaf42ae8bab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="toolstrippanel-control-overview"></a><span data-ttu-id="b379d-102">ToolStripPanel 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b379d-102">ToolStripPanel Control Overview</span></span>
<span data-ttu-id="b379d-103">A<xref:System.Windows.Forms.ToolStripPanel>提供單一區域的定位和浮動定位<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>，和<xref:System.Windows.Forms.StatusStrip>控制項。</span><span class="sxs-lookup"><span data-stu-id="b379d-103">A <xref:System.Windows.Forms.ToolStripPanel> provides a single area for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="b379d-104">多個<xref:System.Windows.Forms.ToolStrip>控制項垂直或水平堆疊取決於<xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A>的<xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="b379d-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically or horizontally depending on the <xref:System.Windows.Forms.ToolStripPanelRow.Orientation%2A> of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>  
  
### <a name="important-toolstrippanel-members"></a><span data-ttu-id="b379d-105">重要 ToolStripPanel 成員</span><span class="sxs-lookup"><span data-stu-id="b379d-105">Important ToolStripPanel Members</span></span>  
  
|<span data-ttu-id="b379d-106">名稱</span><span class="sxs-lookup"><span data-stu-id="b379d-106">Name</span></span>|<span data-ttu-id="b379d-107">說明</span><span class="sxs-lookup"><span data-stu-id="b379d-107">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripPanel.Orientation%2A>|<span data-ttu-id="b379d-108">取得或設定值，指出水平或垂直方向<xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="b379d-108">Gets or sets a value indicating the horizontal or vertical orientation of the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Renderer%2A>|<span data-ttu-id="b379d-109">取得或設定<xref:System.Windows.Forms.ToolStripRenderer>用於自訂的外觀<xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="b379d-109">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance of a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RenderMode%2A>|<span data-ttu-id="b379d-110">取得或設定要套用至的繪製樣式<xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="b379d-110">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.RowMargin%2A>|<span data-ttu-id="b379d-111">取得或設定間距，以像素，之間<xref:System.Windows.Forms.ToolStripPanelRow>和<xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="b379d-111">Gets or sets the spacing, in pixels, between the <xref:System.Windows.Forms.ToolStripPanelRow> and the <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Rows%2A>|<span data-ttu-id="b379d-112">取得<xref:System.Windows.Forms.ToolStripPanelRow>以此<xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="b379d-112">Gets the <xref:System.Windows.Forms.ToolStripPanelRow> in this <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripPanel.Join%2A>|<span data-ttu-id="b379d-113">新增<xref:System.Windows.Forms.ToolStrip>至<xref:System.Windows.Forms.ToolStripPanel>。</span><span class="sxs-lookup"><span data-stu-id="b379d-113">Adds a <xref:System.Windows.Forms.ToolStrip> to a <xref:System.Windows.Forms.ToolStripPanel>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b379d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b379d-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 [<span data-ttu-id="b379d-115">ToolStrip 範例</span><span class="sxs-lookup"><span data-stu-id="b379d-115">ToolStrip Sample</span></span>](http://msdn.microsoft.com/en-us/b7352439-184a-4a3a-b2ad-07465d3af9ed)
