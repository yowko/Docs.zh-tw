---
title: HOW TO：實作自訂配置引擎
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- layout engines [Windows Forms], custom
- TableLayoutPanel control [Windows Forms], layout engine
- layout engines [Windows Forms], implementing
- FlowLayoutPanel control [Windows Forms], layout engine
ms.assetid: f91aa91c-29f4-4089-95ca-5d48b774b00e
ms.openlocfilehash: 8e5043e2b42b1e7449c6dab51691b6d57e28cd53
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59772677"
---
# <a name="how-to-implement-a-custom-layout-engine"></a><span data-ttu-id="e34cb-102">HOW TO：實作自訂配置引擎</span><span class="sxs-lookup"><span data-stu-id="e34cb-102">How to: Implement a Custom Layout Engine</span></span>
<span data-ttu-id="e34cb-103">下列程式碼範例示範如何建立自訂配置引擎執行簡單的流程版面配置。</span><span class="sxs-lookup"><span data-stu-id="e34cb-103">The following code example demonstrates how to create a custom layout engine that performs a simple flow layout.</span></span> <span data-ttu-id="e34cb-104">它會實作名為的面板控制項`DemoFlowPanel`，它會覆寫<xref:System.Windows.Forms.Control.LayoutEngine%2A>屬性提供的執行個體`DemoFlowLayout`類別。</span><span class="sxs-lookup"><span data-stu-id="e34cb-104">It implements a panel control named `DemoFlowPanel`, which overrides the <xref:System.Windows.Forms.Control.LayoutEngine%2A> property to provide an instance of the `DemoFlowLayout` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e34cb-105">範例</span><span class="sxs-lookup"><span data-stu-id="e34cb-105">Example</span></span>  
 [!code-cpp[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/cpp/DemoFlowLayout.cpp#1)]
 [!code-csharp[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/CS/DemoFlowLayout.cs#1)]
 [!code-vb[System.Windows.Forms.Layout.LayoutEngine#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Layout.LayoutEngine/VB/DemoFlowLayout.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e34cb-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e34cb-106">See also</span></span>

- <xref:System.Windows.Forms.Layout.LayoutEngine>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A?displayProperty=nameWithType>
