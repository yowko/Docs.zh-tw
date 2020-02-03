---
title: 在 ListView 控制項中選取專案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 57e985af9d0347510d7d7782f68d5b414d36e077
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743227"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="e9650-102">如何：選取 Windows Form ListView 控制項中的項目</span><span class="sxs-lookup"><span data-stu-id="e9650-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="e9650-103">這個範例示範如何以程式設計方式選取 Windows Forms <xref:System.Windows.Forms.ListView> 控制項中的專案。</span><span class="sxs-lookup"><span data-stu-id="e9650-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="e9650-104">以程式設計方式選取專案，並不會自動將焦點變更為 <xref:System.Windows.Forms.ListView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="e9650-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="e9650-105">因此，在選取專案時，您通常也會想要將專案設定為焦點。</span><span class="sxs-lookup"><span data-stu-id="e9650-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9650-106">範例</span><span class="sxs-lookup"><span data-stu-id="e9650-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e9650-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="e9650-107">Compiling the Code</span></span>  
 <span data-ttu-id="e9650-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="e9650-108">This example requires:</span></span>  
  
- <span data-ttu-id="e9650-109">名為 `listView1` 的 <xref:System.Windows.Forms.ListView> 控制項，其中至少包含一個專案。</span><span class="sxs-lookup"><span data-stu-id="e9650-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
- <span data-ttu-id="e9650-110"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="e9650-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9650-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9650-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
