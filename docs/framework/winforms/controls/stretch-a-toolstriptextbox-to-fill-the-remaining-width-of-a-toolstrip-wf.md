---
title: 如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742836"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="1467d-102">如何：自動縮放 ToolStripTextBox 以填滿 ToolStrip 的剩餘寬度 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="1467d-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="1467d-103">當您將 <xref:System.Windows.Forms.ToolStrip> 控制項的 <xref:System.Windows.Forms.ToolStrip.Stretch%2A> 屬性設定為 [`true`] 時，控制項會從端對端填滿其容器，並在調整其容器大小時調整大小。</span><span class="sxs-lookup"><span data-stu-id="1467d-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="1467d-104">在此設定中，您可能會發現將控制項中的專案（例如 <xref:System.Windows.Forms.ToolStripTextBox>）延伸，以填滿可用的空間，以及調整控制項的大小時，會有很大的説明。</span><span class="sxs-lookup"><span data-stu-id="1467d-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="1467d-105">這項延展功能很有用，例如，如果您想要取得與 Microsoft® Internet Explorer 中的網址列類似的外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="1467d-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1467d-106">範例</span><span class="sxs-lookup"><span data-stu-id="1467d-106">Example</span></span>  
 <span data-ttu-id="1467d-107">下列程式碼範例提供一個衍生自 <xref:System.Windows.Forms.ToolStripTextBox> 的類別，稱為 `ToolStripSpringTextBox`。</span><span class="sxs-lookup"><span data-stu-id="1467d-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="1467d-108">這個類別會覆寫 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> 方法，以便在減去所有其他專案的合併寬度之後，計算父系 <xref:System.Windows.Forms.ToolStrip> 控制項的可用寬度。</span><span class="sxs-lookup"><span data-stu-id="1467d-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="1467d-109">這個程式碼範例也會提供 <xref:System.Windows.Forms.Form> 類別和 `Program` 類別，以示範新的行為。</span><span class="sxs-lookup"><span data-stu-id="1467d-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1467d-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1467d-110">Compiling the Code</span></span>  
 <span data-ttu-id="1467d-111">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="1467d-111">This example requires:</span></span>  
  
- <span data-ttu-id="1467d-112">System、System.Drawing 和 System.Windows.Forms 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="1467d-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1467d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="1467d-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1467d-114">ToolStrip 控制項架構</span><span class="sxs-lookup"><span data-stu-id="1467d-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="1467d-115">操作說明：在 StatusStrip 中以互動方式使用 Spring 屬性</span><span class="sxs-lookup"><span data-stu-id="1467d-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
