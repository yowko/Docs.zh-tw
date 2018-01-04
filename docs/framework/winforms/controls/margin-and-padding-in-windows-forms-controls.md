---
title: "Windows Form 控制項的邊界和邊框距離"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28092704d3c7eaa4820bf6dcbc1678f806ac213e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="81f15-102">Windows Form 控制項的邊界和邊框距離</span><span class="sxs-lookup"><span data-stu-id="81f15-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="81f15-103">對許多應用程式而言，控制項在表單上的精確位置是高優先順序。</span><span class="sxs-lookup"><span data-stu-id="81f15-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="81f15-104"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間提供您許多版面配置功能來完成這項作業。</span><span class="sxs-lookup"><span data-stu-id="81f15-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="81f15-105">最重要的兩項是 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="81f15-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="81f15-106"><xref:System.Windows.Forms.Control.Margin%2A> 屬性可定義控制項周圍的空間，使其他控制項與該控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="81f15-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="81f15-107"><xref:System.Windows.Forms.Control.Padding%2A> 屬性可定義控制項的內部空間，使控制項的內容 (例如，其 <xref:System.Windows.Forms.Control.Text%2A> 屬性值) 與控制項的邊框保持指定的距離。</span><span class="sxs-lookup"><span data-stu-id="81f15-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="81f15-108">下圖顯示控制項上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="81f15-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="81f15-109">![填補和邊界，適用於 Windows Form 控制項](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="81f15-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="81f15-110">Visual Studio 中有針對此功能提供的設計階段支援。</span><span class="sxs-lookup"><span data-stu-id="81f15-110">There is design-time support for this feature in Visual Studio.</span></span>  <span data-ttu-id="81f15-111">另請參閱[逐步解說： 用來配置 Windows Form 控制項的邊框距離、 邊界和 AutoSize 屬性](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="81f15-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f15-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="81f15-112">See Also</span></span>  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
