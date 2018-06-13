---
title: 如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度 (Windows Form)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: bd58cbd109b8e3dd04c6a284dc6926e95830fb61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537716"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="9b21f-102">如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="9b21f-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="9b21f-103">當您將<xref:System.Windows.Forms.ToolStrip.Stretch%2A>屬性<xref:System.Windows.Forms.ToolStrip>控制權傳輸至`true`，控制項從端對端，填滿其容器和其容器調整大小時，調整大小時。</span><span class="sxs-lookup"><span data-stu-id="9b21f-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="9b21f-104">在此組態中，您可能會發現這類延伸項目在控制項中， <xref:System.Windows.Forms.ToolStripTextBox>、 填滿可用空間和調整大小的控制項重新調整大小時。</span><span class="sxs-lookup"><span data-stu-id="9b21f-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="9b21f-105">延伸而非常有用，例如，如果您想要達到的外觀和行為類似於 Microsoft® Internet Explorer 中的網址列。</span><span class="sxs-lookup"><span data-stu-id="9b21f-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b21f-106">範例</span><span class="sxs-lookup"><span data-stu-id="9b21f-106">Example</span></span>  
 <span data-ttu-id="9b21f-107">下列程式碼範例提供一個衍生自類別<xref:System.Windows.Forms.ToolStripTextBox>呼叫`ToolStripSpringTextBox`。</span><span class="sxs-lookup"><span data-stu-id="9b21f-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="9b21f-108">這個類別會覆寫<xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A>方法來計算可用寬度的父代<xref:System.Windows.Forms.ToolStrip>控制項之後已經減去的其他所有項目結合的寬度。</span><span class="sxs-lookup"><span data-stu-id="9b21f-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="9b21f-109">這個程式碼範例也會提供<xref:System.Windows.Forms.Form>類別和`Program`類別來示範新的行為。</span><span class="sxs-lookup"><span data-stu-id="9b21f-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9b21f-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="9b21f-110">Compiling the Code</span></span>  
 <span data-ttu-id="9b21f-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="9b21f-111">This example requires:</span></span>  
  
-   <span data-ttu-id="9b21f-112">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="9b21f-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b21f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b21f-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="9b21f-114">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="9b21f-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="9b21f-115">操作說明：在 StatusStrip 中以互動方式使用 Spring 屬性</span><span class="sxs-lookup"><span data-stu-id="9b21f-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
