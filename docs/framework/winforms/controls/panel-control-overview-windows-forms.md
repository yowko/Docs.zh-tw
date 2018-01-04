---
title: "Panel 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8855c88a0ec60cd0d44d73046e44c9614347d90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="panel-control-overview-windows-forms"></a><span data-ttu-id="b2e2b-102">Panel 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="b2e2b-102">Panel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="b2e2b-103">Windows Form<xref:System.Windows.Forms.Panel>控制項可用來提供其他控制項可識別的群組。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to provide an identifiable grouping for other controls.</span></span> <span data-ttu-id="b2e2b-104">一般而言，您可以使用面板細分函式表單。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-104">Typically, you use panels to subdivide a form by function.</span></span> <span data-ttu-id="b2e2b-105">比方說，您可能會指定郵寄選項，例如要使用哪個夜間貨運訂購表單。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-105">For example, you may have an order form that specifies mailing options such as which overnight carrier to use.</span></span> <span data-ttu-id="b2e2b-106">將在面板中的所有選項，可讓使用者邏輯的視覺提示。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-106">Grouping all options in a panel gives the user a logical visual cue.</span></span> <span data-ttu-id="b2e2b-107">在設計階段控制項可以輕易地移動所有 — 當您移動<xref:System.Windows.Forms.Panel>控制所有其包含的控制項，跟著移動。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-107">At design time all the controls can be moved easily — when you move the <xref:System.Windows.Forms.Panel> control, all its contained controls move, too.</span></span> <span data-ttu-id="b2e2b-108">可以透過存取面板中分組的控制項及其<xref:System.Windows.Forms.Control.Controls%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-108">The controls grouped in a panel can be accessed through its <xref:System.Windows.Forms.Control.Controls%2A> property.</span></span> <span data-ttu-id="b2e2b-109">這個屬性傳回的集合<xref:System.Windows.Forms.Control>執行個體，因此您通常需要轉型控制項擷取這種方式為其特定的型別。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-109">This property returns a collection of <xref:System.Windows.Forms.Control> instances, so you will typically need to cast a control retrieved this way to its specific type.</span></span>  
  
## <a name="panel-versus-groupbox"></a><span data-ttu-id="b2e2b-110">GroupBox 與面板</span><span class="sxs-lookup"><span data-stu-id="b2e2b-110">Panel Versus GroupBox</span></span>  
 <span data-ttu-id="b2e2b-111"><xref:System.Windows.Forms.Panel>控制項是類似於<xref:System.Windows.Forms.GroupBox>控制項等控制項，不過，只有<xref:System.Windows.Forms.Panel>控制項有捲軸僅限和<xref:System.Windows.Forms.GroupBox>控制項顯示的標題。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-111">The <xref:System.Windows.Forms.Panel> control is similar to the <xref:System.Windows.Forms.GroupBox> control; however, only the <xref:System.Windows.Forms.Panel> control can have scroll bars, and only the <xref:System.Windows.Forms.GroupBox> control displays a caption.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="b2e2b-112">索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="b2e2b-112">Key Properties</span></span>  
 <span data-ttu-id="b2e2b-113">若要顯示捲軸，設定<xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A>屬性`true`。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-113">To display scroll bars, set the <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> property to `true`.</span></span> <span data-ttu-id="b2e2b-114">您也可以藉由設定自訂面板的外觀<xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.BackgroundImage%2A>，和<xref:System.Windows.Forms.Panel.BorderStyle%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-114">You can also customize the appearance of the panel by setting the <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, and <xref:System.Windows.Forms.Panel.BorderStyle%2A> properties.</span></span> <span data-ttu-id="b2e2b-115">如需有關<xref:System.Windows.Forms.Control.BackColor%2A>和<xref:System.Windows.Forms.Control.BackgroundImage%2A>屬性，請參閱[How to： 設定面板的背景](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md)。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-115">For more information on the <xref:System.Windows.Forms.Control.BackColor%2A> and <xref:System.Windows.Forms.Control.BackgroundImage%2A> properties, see [How to: Set the Background of a Panel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).</span></span> <span data-ttu-id="b2e2b-116"><xref:System.Windows.Forms.Panel.BorderStyle%2A>屬性會決定是否看不到框線與概述面板 (<xref:System.Windows.Forms.BorderStyle.None>)，純文字的一行 (<xref:System.Windows.Forms.BorderStyle.FixedSingle>)，或加上陰影的列 (<xref:System.Windows.Forms.BorderStyle.Fixed3D>)。</span><span class="sxs-lookup"><span data-stu-id="b2e2b-116">The <xref:System.Windows.Forms.Panel.BorderStyle%2A> property determines if the panel is outlined with no visible border (<xref:System.Windows.Forms.BorderStyle.None>), a plain line (<xref:System.Windows.Forms.BorderStyle.FixedSingle>), or a shadowed line (<xref:System.Windows.Forms.BorderStyle.Fixed3D>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e2b-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="b2e2b-117">See Also</span></span>  
 <xref:System.Windows.Forms.Panel>  
 [<span data-ttu-id="b2e2b-118">GroupBox 控制項</span><span class="sxs-lookup"><span data-stu-id="b2e2b-118">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)  
 [<span data-ttu-id="b2e2b-119">操作說明：搭配 Windows Forms Panel 控制項使用設計工具群組控制項</span><span class="sxs-lookup"><span data-stu-id="b2e2b-119">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)  
 [<span data-ttu-id="b2e2b-120">操作說明：使用設計工具設定 Windows Forms 面板的背景</span><span class="sxs-lookup"><span data-stu-id="b2e2b-120">How to: Set the Background of a Windows Forms Panel Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
