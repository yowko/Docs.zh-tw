---
title: DomainUpDown 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965305"
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="feb33-102">DomainUpDown 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="feb33-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="feb33-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown>控制項基本上是文字方塊和一對按鈕的組合, 可在清單中向上或向下移動。</span><span class="sxs-lookup"><span data-stu-id="feb33-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="feb33-104">控制項會顯示並設定挑選清單中的文字字串。</span><span class="sxs-lookup"><span data-stu-id="feb33-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="feb33-105">使用者可以選取字串, 方法是按一下向上和向下按鈕以移動清單、按向上鍵和向下鍵, 或輸入符合清單中專案的字串。</span><span class="sxs-lookup"><span data-stu-id="feb33-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="feb33-106">此控制項的其中一個可能用途是從依字母順序排序的名稱清單中選取專案。</span><span class="sxs-lookup"><span data-stu-id="feb33-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="feb33-107">若要排序清單, 請將<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性設定`true`為。</span><span class="sxs-lookup"><span data-stu-id="feb33-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="feb33-108">此控制項的功能與清單方塊或下拉式方塊非常類似, 但佔用的空間非常少。</span><span class="sxs-lookup"><span data-stu-id="feb33-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="feb33-109">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="feb33-109">Key Properties</span></span>  
 <span data-ttu-id="feb33-110">控制項的索引鍵屬性為<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。</span><span class="sxs-lookup"><span data-stu-id="feb33-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="feb33-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含物件的清單, 其文字值會顯示在控制項中。</span><span class="sxs-lookup"><span data-stu-id="feb33-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="feb33-112">如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設定為`false`, 控制項會自動完成使用者輸入的文字, 並將其與清單中的值比對。</span><span class="sxs-lookup"><span data-stu-id="feb33-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="feb33-113">如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設定為`true`, 則在最後一個專案之後的滾動會帶您前往清單中的第一個專案, 反之亦然。</span><span class="sxs-lookup"><span data-stu-id="feb33-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="feb33-114">控制項的主要方法是<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和。 <xref:System.Windows.Forms.DomainUpDown.DownButton%2A></span><span class="sxs-lookup"><span data-stu-id="feb33-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="feb33-115">此控制項只會顯示文字字串。</span><span class="sxs-lookup"><span data-stu-id="feb33-115">This control displays only text strings.</span></span> <span data-ttu-id="feb33-116">如果您想要顯示數值的控制項, 請使用<xref:System.Windows.Forms.NumericUpDown>控制項。</span><span class="sxs-lookup"><span data-stu-id="feb33-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="feb33-117">如需詳細資訊, 請參閱[NumericUpDown 控制項總覽](numericupdown-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="feb33-117">For more information, see [NumericUpDown Control Overview](numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb33-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feb33-118">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- [<span data-ttu-id="feb33-119">DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="feb33-119">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
