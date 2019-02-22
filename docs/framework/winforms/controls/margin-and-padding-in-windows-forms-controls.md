---
title: Windows Form 控制項的邊界和邊框距離
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: a3218ad029735f4a5d70b3166951dcd93e061c26
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665221"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="20f85-102">Windows Form 控制項的邊界和邊框距離</span><span class="sxs-lookup"><span data-stu-id="20f85-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="20f85-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="20f85-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="20f85-104"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間提供您許多版面配置功能來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="20f85-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="20f85-105">最重要的兩項是 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="20f85-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="20f85-106"><xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="20f85-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="20f85-107"><xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 (例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值) 與控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="20f85-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="20f85-108">下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="20f85-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="20f85-109">![邊框距離及邊界 Windows Forms 控制項](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="20f85-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="20f85-110">Visual Studio 中有針對此功能提供的設計階段支援。</span><span class="sxs-lookup"><span data-stu-id="20f85-110">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="20f85-111">另請參閱[逐步解說：配置 Windows Form 控制項與邊框距離、 邊界和 AutoSize 屬性](windows-forms-controls-padding-autosize.md)。</span><span class="sxs-lookup"><span data-stu-id="20f85-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f85-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20f85-112">See also</span></span>
- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
