---
title: "DomainUpDown 控制項 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 485640dc320809e9be5550d380b4fc9a2326e027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="801c6-102">DomainUpDown 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="801c6-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="801c6-103">Windows Form<xref:System.Windows.Forms.DomainUpDown>控制項看起來對按鈕及文字方塊中的組合的清單中向上或向下移動。</span><span class="sxs-lookup"><span data-stu-id="801c6-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="801c6-104">控制項顯示，並設定選項的清單中的文字字串。</span><span class="sxs-lookup"><span data-stu-id="801c6-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="801c6-105">按一下向上和向下按鈕移動清單、 按向上鍵和向下鍵，或輸入清單中的項目相符的字串，使用者可以選取的字串。</span><span class="sxs-lookup"><span data-stu-id="801c6-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="801c6-106">這個控制項的其中一個可能的使用是從依字母順序排序的名稱清單中選取項目。</span><span class="sxs-lookup"><span data-stu-id="801c6-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="801c6-107">(若要排序清單，請設定<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性`true`。)這個控制項的功能清單方塊或下拉式方塊中，非常類似，但是它會佔用很少的空間。</span><span class="sxs-lookup"><span data-stu-id="801c6-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="801c6-108">控制項的索引鍵屬性是<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。</span><span class="sxs-lookup"><span data-stu-id="801c6-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="801c6-109"><xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含的控制項中顯示其文字值的物件清單。</span><span class="sxs-lookup"><span data-stu-id="801c6-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="801c6-110">如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設`false`，控制項時自動完成文字使用者輸入，然後進行比對清單中的值。</span><span class="sxs-lookup"><span data-stu-id="801c6-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="801c6-111">如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設`true`，過去的最後一個項目捲動會帶您前往第一個項目在清單中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="801c6-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="801c6-112">控制項的主要方法是<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。</span><span class="sxs-lookup"><span data-stu-id="801c6-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="801c6-113">此控制項顯示只是文字字串。</span><span class="sxs-lookup"><span data-stu-id="801c6-113">This control displays only text strings.</span></span> <span data-ttu-id="801c6-114">如果您想要顯示數值的控制項，使用<xref:System.Windows.Forms.NumericUpDown>控制項。</span><span class="sxs-lookup"><span data-stu-id="801c6-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="801c6-115">如需詳細資訊，請參閱[NumericUpDown 控制項](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="801c6-115">For more information, see [NumericUpDown Control](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="801c6-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="801c6-116">In This Section</span></span>  
 [<span data-ttu-id="801c6-117">DomainUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="801c6-117">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="801c6-118">導入的一般概念<xref:System.Windows.Forms.DomainUpDown>控制項，可讓使用者瀏覽並選取從文字字串的清單。</span><span class="sxs-lookup"><span data-stu-id="801c6-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 [<span data-ttu-id="801c6-119">操作說明：以程式設計的方式將項目加入至 Windows Forms DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="801c6-119">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <span data-ttu-id="801c6-120">描述如何指定文字字串<xref:System.Windows.Forms.DomainUpDown>控制項應顯示。</span><span class="sxs-lookup"><span data-stu-id="801c6-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="801c6-121">操作說明：從 Windows Forms DomainUpDown 控制項中移除項目</span><span class="sxs-lookup"><span data-stu-id="801c6-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="801c6-122">描述如何刪除項目從<xref:System.Windows.Forms.DomainUpDown>程式碼中的控制項。</span><span class="sxs-lookup"><span data-stu-id="801c6-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="801c6-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="801c6-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="801c6-124">描述這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="801c6-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="801c6-125">描述這個類別，並且提供其所有成員都的連結...</span><span class="sxs-lookup"><span data-stu-id="801c6-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="801c6-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="801c6-126">Related Sections</span></span>  
 [<span data-ttu-id="801c6-127">可以在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="801c6-127">Controls You Can Use On Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="801c6-128">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="801c6-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
