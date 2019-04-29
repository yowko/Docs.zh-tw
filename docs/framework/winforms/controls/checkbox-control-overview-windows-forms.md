---
title: CheckBox 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: 2a18327d9836d1dbbcd5d5d6e73f217637736d20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938966"
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="8b713-102">CheckBox 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="8b713-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="8b713-103">Windows Form <xref:System.Windows.Forms.CheckBox> 控制項表示特定的條件是開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="8b713-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="8b713-104">它通常用來呈現是/否或 True/False 選取項目給使用者。</span><span class="sxs-lookup"><span data-stu-id="8b713-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="8b713-105">您可以使用群組中的核取方塊控制項來顯示使用者可以從中選取一個或多個的多重選擇。</span><span class="sxs-lookup"><span data-stu-id="8b713-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="8b713-106">核取方塊控制項是類似於選項按鈕控制項都用來指示使用者所做的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="8b713-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="8b713-107">它們之間的差異在於只能有一個選項按鈕群組中的可以選取一次。</span><span class="sxs-lookup"><span data-stu-id="8b713-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="8b713-108">與核取方塊控制項，不過，任何數目的核取方塊可能會選取。</span><span class="sxs-lookup"><span data-stu-id="8b713-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="8b713-109">核取方塊可能連接到在資料庫中使用簡單資料繫結的項目。</span><span class="sxs-lookup"><span data-stu-id="8b713-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="8b713-110">多個核取方塊可能使用分組<xref:System.Windows.Forms.GroupBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="8b713-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="8b713-111">這是視覺外觀以及使用者介面的設計，非常有用，因為群組的控制項可以同時移動表單設計工具上。</span><span class="sxs-lookup"><span data-stu-id="8b713-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="8b713-112">如需詳細資訊，請參閱 < [Windows Forms 資料繫結](../windows-forms-data-binding.md)並[GroupBox 控制項](groupbox-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="8b713-112">For more information, see [Windows Forms Data Binding](../windows-forms-data-binding.md) and [GroupBox Control](groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="8b713-113"><xref:System.Windows.Forms.CheckBox>控制項有兩個重要屬性，<xref:System.Windows.Forms.CheckBox.Checked%2A>和<xref:System.Windows.Forms.CheckBox.CheckState%2A>。</span><span class="sxs-lookup"><span data-stu-id="8b713-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="8b713-114"><xref:System.Windows.Forms.CheckBox.Checked%2A>屬性會傳回`true`或`false`。</span><span class="sxs-lookup"><span data-stu-id="8b713-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="8b713-115"><xref:System.Windows.Forms.CheckBox.CheckState%2A>屬性會傳回<xref:System.Windows.Forms.CheckState.Checked>或是<xref:System.Windows.Forms.CheckState.Unchecked>; 或者，如果<xref:System.Windows.Forms.CheckBox.ThreeState%2A>屬性設定為`true`，<xref:System.Windows.Forms.CheckBox.CheckState%2A>也可能會傳回<xref:System.Windows.Forms.CheckState.Indeterminate>。</span><span class="sxs-lookup"><span data-stu-id="8b713-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="8b713-116">處於不定狀態，方塊會顯示呈現暗灰色的外觀，以表示無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8b713-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b713-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b713-117">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="8b713-118">如何：設定使用 Windows Form 核取方塊控制項的選項</span><span class="sxs-lookup"><span data-stu-id="8b713-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="8b713-119">如何：回應 Windows Form CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="8b713-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="8b713-120">CheckBox 控制項</span><span class="sxs-lookup"><span data-stu-id="8b713-120">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
