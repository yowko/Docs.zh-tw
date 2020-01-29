---
title: CheckBox 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
ms.openlocfilehash: b42816cf1bc0ce1ab6db0a2a436b17b0d4370d59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737102"
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="31509-102">CheckBox 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="31509-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="31509-103">Windows Form <xref:System.Windows.Forms.CheckBox> 控制項表示特定的條件是開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="31509-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="31509-104">它通常用來呈現是/否或 True/False 選取項目給使用者。</span><span class="sxs-lookup"><span data-stu-id="31509-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="31509-105">您可以使用群組中的核取方塊控制項來顯示使用者可以從中選取一個或多個的多重選擇。</span><span class="sxs-lookup"><span data-stu-id="31509-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="31509-106">核取方塊控制項類似于選項按鈕控制項，其中每個控制項會用來表示使用者所做的選擇。</span><span class="sxs-lookup"><span data-stu-id="31509-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="31509-107">兩者不同之處在于，一次只能選取一個群組中的一個選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="31509-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="31509-108">不過，您可以使用核取方塊控制項，選取任意數目的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="31509-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="31509-109">您可以使用簡單的資料系結，將核取方塊連接到資料庫中的元素。</span><span class="sxs-lookup"><span data-stu-id="31509-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="31509-110">您可以使用 <xref:System.Windows.Forms.GroupBox> 控制項，將多個核取方塊分組。</span><span class="sxs-lookup"><span data-stu-id="31509-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="31509-111">這適用于視覺外觀，也適用于使用者介面設計，因為群組控制項可以在表單設計工具上四處移動。</span><span class="sxs-lookup"><span data-stu-id="31509-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="31509-112">如需詳細資訊，請參閱[Windows Forms 資料](../windows-forms-data-binding.md)系結和[分組控制項](groupbox-control-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="31509-112">For more information, see [Windows Forms Data Binding](../windows-forms-data-binding.md) and [GroupBox Control](groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="31509-113"><xref:System.Windows.Forms.CheckBox> 控制項有兩個重要的屬性： <xref:System.Windows.Forms.CheckBox.Checked%2A> 和 <xref:System.Windows.Forms.CheckBox.CheckState%2A>。</span><span class="sxs-lookup"><span data-stu-id="31509-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="31509-114"><xref:System.Windows.Forms.CheckBox.Checked%2A> 屬性會傳回 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="31509-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="31509-115"><xref:System.Windows.Forms.CheckBox.CheckState%2A> 屬性會傳回 <xref:System.Windows.Forms.CheckState.Checked> 或 <xref:System.Windows.Forms.CheckState.Unchecked>;或者，如果 <xref:System.Windows.Forms.CheckBox.ThreeState%2A> 屬性設為 `true`，<xref:System.Windows.Forms.CheckBox.CheckState%2A> 也會傳回 <xref:System.Windows.Forms.CheckState.Indeterminate>。</span><span class="sxs-lookup"><span data-stu-id="31509-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="31509-116">在 [不定] 狀態中，方塊會以暗灰色的外觀顯示，表示無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="31509-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31509-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="31509-117">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="31509-118">操作說明：使用 Windows Forms CheckBox 控制項設定選項</span><span class="sxs-lookup"><span data-stu-id="31509-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](how-to-set-options-with-windows-forms-checkbox-controls.md)
- [<span data-ttu-id="31509-119">操作說明：回應 Windows Forms CheckBox 按一下動作</span><span class="sxs-lookup"><span data-stu-id="31509-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="31509-120">CheckBox 控制項</span><span class="sxs-lookup"><span data-stu-id="31509-120">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
