---
title: "如何：選取 Windows Form ListView 控制項中的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef672dc909717ba979d81bd98510dad6419583a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="ff66c-102">如何：選取 Windows Form ListView 控制項中的項目</span><span class="sxs-lookup"><span data-stu-id="ff66c-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="ff66c-103">這個範例示範如何以程式設計方式在 Windows Form 中選取的項目<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="ff66c-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="ff66c-104">以程式設計方式選取項目不會自動變更焦點<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="ff66c-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="ff66c-105">基於這個理由，您通常也要設定的項目，因為已取得焦點時選取項目。</span><span class="sxs-lookup"><span data-stu-id="ff66c-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff66c-106">範例</span><span class="sxs-lookup"><span data-stu-id="ff66c-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff66c-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="ff66c-107">Compiling the Code</span></span>  
 <span data-ttu-id="ff66c-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="ff66c-108">This example requires:</span></span>  
  
-   <span data-ttu-id="ff66c-109">A<xref:System.Windows.Forms.ListView>控制項，名為`listView1`，其中包含至少一個項目。</span><span class="sxs-lookup"><span data-stu-id="ff66c-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="ff66c-110"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="ff66c-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff66c-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="ff66c-111">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
