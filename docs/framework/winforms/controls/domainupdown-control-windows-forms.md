---
title: DomainUpDown 控制項 (Windows Form)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: 83d674e3fb7ff7e715b75c635b891cd4e9703a21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972051"
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="40bdc-102">DomainUpDown 控制項 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="40bdc-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="40bdc-103">Windows Form<xref:System.Windows.Forms.DomainUpDown>控制項看起來像組合的文字方塊和按鈕的清單中向上或向下移動。</span><span class="sxs-lookup"><span data-stu-id="40bdc-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="40bdc-104">控制項顯示，並從清單中選擇設定文字字串。</span><span class="sxs-lookup"><span data-stu-id="40bdc-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="40bdc-105">按一下向上和向下按鈕移動清單、 按下向上鍵和向下鍵，或輸入字串符合清單中的項目，使用者可以選取字串。</span><span class="sxs-lookup"><span data-stu-id="40bdc-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="40bdc-106">這個控制項的可能用法之一是從名稱依字母順序排序清單中選取項目。</span><span class="sxs-lookup"><span data-stu-id="40bdc-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="40bdc-107">(若要排序的清單，請設定<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性設`true`。)這個控制項的函式的清單方塊或下拉式方塊中，非常類似，但是它會佔用很少的空間。</span><span class="sxs-lookup"><span data-stu-id="40bdc-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="40bdc-108">控制項的索引鍵屬性是<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。</span><span class="sxs-lookup"><span data-stu-id="40bdc-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="40bdc-109"><xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含的控制項中所顯示的文字值的物件清單。</span><span class="sxs-lookup"><span data-stu-id="40bdc-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="40bdc-110">如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設為`false`，控制項自動完成文字的使用者類型，並比對清單中的值。</span><span class="sxs-lookup"><span data-stu-id="40bdc-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="40bdc-111">如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設為`true`，過去的最後一個項目捲動會帶您前往第一個項目清單中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="40bdc-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="40bdc-112">控制項的主要方法會<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。</span><span class="sxs-lookup"><span data-stu-id="40bdc-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="40bdc-113">此控制項會顯示只是文字字串。</span><span class="sxs-lookup"><span data-stu-id="40bdc-113">This control displays only text strings.</span></span> <span data-ttu-id="40bdc-114">如果您想要顯示數值的控制項，使用<xref:System.Windows.Forms.NumericUpDown>控制項。</span><span class="sxs-lookup"><span data-stu-id="40bdc-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="40bdc-115">如需詳細資訊，請參閱 < [NumericUpDown 控制項](numericupdown-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="40bdc-115">For more information, see [NumericUpDown Control](numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40bdc-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="40bdc-116">In This Section</span></span>  
 [<span data-ttu-id="40bdc-117">DomainUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="40bdc-117">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="40bdc-118">導入的一般概念<xref:System.Windows.Forms.DomainUpDown>控制項，可讓使用者瀏覽和選取從文字字串的清單。</span><span class="sxs-lookup"><span data-stu-id="40bdc-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 [<span data-ttu-id="40bdc-119">如何：以程式設計方式將項目加入 Windows Form DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="40bdc-119">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>](how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <span data-ttu-id="40bdc-120">描述如何指定文字字串<xref:System.Windows.Forms.DomainUpDown>控制項應顯示。</span><span class="sxs-lookup"><span data-stu-id="40bdc-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="40bdc-121">如何：移除 Windows Form DomainUpDown 控制項中的項目</span><span class="sxs-lookup"><span data-stu-id="40bdc-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="40bdc-122">描述如何刪除項目從<xref:System.Windows.Forms.DomainUpDown>在程式碼中的控制項。</span><span class="sxs-lookup"><span data-stu-id="40bdc-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="40bdc-123">參考資料</span><span class="sxs-lookup"><span data-stu-id="40bdc-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="40bdc-124">說明這個類別，並且提供其所有成員的連結。</span><span class="sxs-lookup"><span data-stu-id="40bdc-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="40bdc-125">描述這個類別並且連結到其所有成員...</span><span class="sxs-lookup"><span data-stu-id="40bdc-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40bdc-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="40bdc-126">Related Sections</span></span>  
 [<span data-ttu-id="40bdc-127">可以在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="40bdc-127">Controls You Can Use On Windows Forms</span></span>](controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="40bdc-128">提供 Windows Form 控制項的完整清單，以及其用法的資訊連結。</span><span class="sxs-lookup"><span data-stu-id="40bdc-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
