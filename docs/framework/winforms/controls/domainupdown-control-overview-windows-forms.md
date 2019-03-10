---
title: DomainUpDown 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 851c02747a2414e34a5e9d35bdc7d1df916efce0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718892"
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="9596b-102">DomainUpDown 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9596b-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="9596b-103">Windows Form<xref:System.Windows.Forms.DomainUpDown>控制項是本質上的文字方塊中的組合以及一組按鈕清單中向上或向下移動。</span><span class="sxs-lookup"><span data-stu-id="9596b-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="9596b-104">控制項顯示，並從清單中選擇設定文字字串。</span><span class="sxs-lookup"><span data-stu-id="9596b-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="9596b-105">按一下向上和向下按鈕移動清單、 按下向上鍵和向下鍵，或輸入字串符合清單中的項目，使用者可以選取字串。</span><span class="sxs-lookup"><span data-stu-id="9596b-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="9596b-106">這個控制項的可能用法之一是從名稱依字母順序排序清單中選取項目。</span><span class="sxs-lookup"><span data-stu-id="9596b-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9596b-107">若要排序的清單，請設定<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="9596b-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="9596b-108">這個控制項的函式的清單方塊或下拉式方塊中，非常類似，但是它會佔用很少的空間。</span><span class="sxs-lookup"><span data-stu-id="9596b-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="9596b-109">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="9596b-109">Key Properties</span></span>  
 <span data-ttu-id="9596b-110">控制項的索引鍵屬性是<xref:System.Windows.Forms.DomainUpDown.Items%2A>， <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>，和<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>。</span><span class="sxs-lookup"><span data-stu-id="9596b-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="9596b-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A>屬性包含的控制項中所顯示的文字值的物件清單。</span><span class="sxs-lookup"><span data-stu-id="9596b-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="9596b-112">如果<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>設為`false`，控制項自動完成文字的使用者類型，並比對清單中的值。</span><span class="sxs-lookup"><span data-stu-id="9596b-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="9596b-113">如果<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>設為`true`，過去的最後一個項目捲動會帶您前往第一個項目清單中，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="9596b-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="9596b-114">控制項的主要方法會<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>和<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>。</span><span class="sxs-lookup"><span data-stu-id="9596b-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="9596b-115">此控制項會顯示只是文字字串。</span><span class="sxs-lookup"><span data-stu-id="9596b-115">This control displays only text strings.</span></span> <span data-ttu-id="9596b-116">如果您想要顯示數值的控制項，使用<xref:System.Windows.Forms.NumericUpDown>控制項。</span><span class="sxs-lookup"><span data-stu-id="9596b-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="9596b-117">如需詳細資訊，請參閱 < [NumericUpDown 控制項概觀](numericupdown-control-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="9596b-117">For more information, see [NumericUpDown Control Overview](numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9596b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9596b-118">See also</span></span>
- <xref:System.Windows.Forms.DomainUpDown>
- [<span data-ttu-id="9596b-119">DomainUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="9596b-119">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
