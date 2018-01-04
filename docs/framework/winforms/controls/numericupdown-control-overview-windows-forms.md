---
title: "NumericUpDown 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NumericUpDown
helpviewer_keywords:
- numeric spin button control [Windows Forms], Windows Forms
- NumericUpDown control [Windows Forms], about NumericUpDown control
- spin button control [Windows Forms], Windows Forms
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 067a8862ee991213e584819e1cf99eddde06e2bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="numericupdown-control-overview-windows-forms"></a><span data-ttu-id="ccead-102">NumericUpDown 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="ccead-102">NumericUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="ccead-103"><xref:System.Windows.Forms.NumericUpDown>控制項看起來像文字方塊中的組合和一對箭號，讓使用者可以按一下以調整值。</span><span class="sxs-lookup"><span data-stu-id="ccead-103">The <xref:System.Windows.Forms.NumericUpDown> control looks like a combination of a text box and a pair of arrows that the user can click to adjust a value.</span></span> <span data-ttu-id="ccead-104">控制項顯示，並設定單一數值的數字值的固定選擇清單中。</span><span class="sxs-lookup"><span data-stu-id="ccead-104">The control displays and sets a single numeric value from a list of fixed numeric-value choices.</span></span> <span data-ttu-id="ccead-105">使用者可以增加和減少數目，依序按一下向上和向下箭號，按向上鍵和向下鍵，或在控制項中輸入數字。</span><span class="sxs-lookup"><span data-stu-id="ccead-105">The user can increase and decrease the number by clicking the up and down arrows, by pressing the UP and DOWN ARROW keys, or by typing a number in the text box part of the control.</span></span> <span data-ttu-id="ccead-106">按一下向上鍵移動朝最大值。按一下向下鍵移動朝最小值。</span><span class="sxs-lookup"><span data-stu-id="ccead-106">Clicking the UP ARROW key moves the number toward the maximum; clicking the DOWN ARROW key moves the number toward the minimum.</span></span>  
  
 <span data-ttu-id="ccead-107">具有靈活的功能，因為此控制項是明顯的選項，例如，如果您想要建立音樂的播放器應用程式的音量控制項。</span><span class="sxs-lookup"><span data-stu-id="ccead-107">Because of its versatile functionality, this control is an obvious choice, for example, if you want to create a volume control for a music player application.</span></span> <span data-ttu-id="ccead-108"><xref:System.Windows.Forms.NumericUpDown>控制項用在許多 Windows 控制台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ccead-108">The <xref:System.Windows.Forms.NumericUpDown> control is used in many Windows Control Panel applications.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="ccead-109">索引鍵屬性和方法</span><span class="sxs-lookup"><span data-stu-id="ccead-109">Key Properties and Methods</span></span>  
 <span data-ttu-id="ccead-110">在控制項的文字方塊中顯示的數字可以是各種不同的格式，包括十六進位。</span><span class="sxs-lookup"><span data-stu-id="ccead-110">The numbers displayed in the control's text box can be in a variety of formats, including hexadecimal.</span></span> <span data-ttu-id="ccead-111">如需詳細資訊，請參閱[How to： 設定 Windows Form NumericUpDown 控制項的格式](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)。</span><span class="sxs-lookup"><span data-stu-id="ccead-111">For more information, see [How to: Set the Format for the Windows Forms NumericUpDown Control](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md).</span></span> <span data-ttu-id="ccead-112">控制項的索引鍵屬性是<xref:System.Windows.Forms.NumericUpDown.Value%2A>， <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> （預設值 100） <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> （預設值為 0） 和<xref:System.Windows.Forms.NumericUpDown.Increment%2A>（預設值 1）。</span><span class="sxs-lookup"><span data-stu-id="ccead-112">The key properties of the control are <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> (default value 100), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> (default value 0), and <xref:System.Windows.Forms.NumericUpDown.Increment%2A> (default value 1).</span></span> <span data-ttu-id="ccead-113"><xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性設定控制項中選取的目前數目。</span><span class="sxs-lookup"><span data-stu-id="ccead-113">The <xref:System.Windows.Forms.NumericUpDown.Value%2A> property sets the current number selected in the control.</span></span> <span data-ttu-id="ccead-114"><xref:System.Windows.Forms.NumericUpDown.Increment%2A>屬性會設定當使用者按一下向上或向下箭號調整的數字量。</span><span class="sxs-lookup"><span data-stu-id="ccead-114">The <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property sets the amount that the number is adjusted by when the user clicks an up or down arrow.</span></span> <span data-ttu-id="ccead-115">當焦點離開控制項時，任何輸入將會驗證最小和最大的數字值。</span><span class="sxs-lookup"><span data-stu-id="ccead-115">When focus moves off the control, any typed input will be validated against the minimum and maximum numeric values.</span></span> <span data-ttu-id="ccead-116">您可以增加時，使用者持續按下向上或向下箭號的數字，移動控制項的速度與<xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ccead-116">You can increase the speed that the control moves through numbers, when the user continuously presses the up or down arrow, with the <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A> property.</span></span> <span data-ttu-id="ccead-117">控制項的主要方法是<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>和<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>。</span><span class="sxs-lookup"><span data-stu-id="ccead-117">The key methods of the control are <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccead-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ccead-118">See Also</span></span>  
 <xref:System.Windows.Forms.NumericUpDown>  
 [<span data-ttu-id="ccead-119">NumericUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="ccead-119">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [<span data-ttu-id="ccead-120">操作說明：為 Windows Forms NumericUpDown 控制項設定格式</span><span class="sxs-lookup"><span data-stu-id="ccead-120">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)  
 [<span data-ttu-id="ccead-121">TextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="ccead-121">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
