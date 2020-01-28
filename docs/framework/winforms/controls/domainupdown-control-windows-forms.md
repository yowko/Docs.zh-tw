---
title: DomainUpDown 控制項
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: b538350a84e341d6b2759a7db28f8799f3777a86
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745835"
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="f0a7c-102">DomainUpDown 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="f0a7c-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="f0a7c-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> 控制項看起來像是文字方塊和一對按鈕的組合，可在清單中向上或向下移動。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="f0a7c-104">控制項會顯示並設定挑選清單中的文字字串。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="f0a7c-105">使用者可以選取字串，方法是按一下向上和向下按鈕以移動清單、按向上鍵和向下鍵，或輸入符合清單中專案的字串。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="f0a7c-106">此控制項的其中一個可能用途是從依字母順序排序的名稱清單中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="f0a7c-107">（若要排序清單，請將 [<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>] 屬性設定為 [`true`]）。此控制項的功能與清單方塊或下拉式方塊非常類似，但佔用的空間非常少。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="f0a7c-108">控制項的索引鍵屬性為 <xref:System.Windows.Forms.DomainUpDown.Items%2A>、<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>和 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="f0a7c-109"><xref:System.Windows.Forms.DomainUpDown.Items%2A> 屬性包含其文字值顯示在控制項中的物件清單。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="f0a7c-110">如果 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> 設定為 [`false`]，控制項會自動完成使用者輸入的文字，並將其與清單中的值比對。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="f0a7c-111">如果 <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> 設定為 `true`，則在最後一個專案之後的滾動會帶您前往清單中的第一個專案，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="f0a7c-112">控制項的主要方法是 <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="f0a7c-113">此控制項只會顯示文字字串。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-113">This control displays only text strings.</span></span> <span data-ttu-id="f0a7c-114">如果您想要顯示數值的控制項，請使用 <xref:System.Windows.Forms.NumericUpDown> 控制項。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="f0a7c-115">如需詳細資訊，請參閱[NumericUpDown Control](numericupdown-control-windows-forms.md) 。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-115">For more information, see [NumericUpDown Control](numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f0a7c-116">本章節內容</span><span class="sxs-lookup"><span data-stu-id="f0a7c-116">In This Section</span></span>  
 [<span data-ttu-id="f0a7c-117">DomainUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="f0a7c-117">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="f0a7c-118">介紹 <xref:System.Windows.Forms.DomainUpDown> 控制項的一般概念，可讓使用者流覽並從文字字串清單中選取。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 [<span data-ttu-id="f0a7c-119">操作說明：以程式設計的方式將項目加入至 Windows Forms DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="f0a7c-119">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <span data-ttu-id="f0a7c-120">描述如何指定 <xref:System.Windows.Forms.DomainUpDown> 控制項應顯示的文字字串。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="f0a7c-121">操作說明：從 Windows Forms DomainUpDown 控制項中移除項目</span><span class="sxs-lookup"><span data-stu-id="f0a7c-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="f0a7c-122">描述如何在程式碼中刪除 <xref:System.Windows.Forms.DomainUpDown> 控制項的專案。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f0a7c-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="f0a7c-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="f0a7c-124">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="f0a7c-125">描述這個類別，並具有其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f0a7c-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="f0a7c-126">Related Sections</span></span>  
 [<span data-ttu-id="f0a7c-127">可以在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="f0a7c-127">Controls You Can Use On Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="f0a7c-128">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="f0a7c-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
