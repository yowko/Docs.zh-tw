---
title: HOW TO：選取 Windows Forms ListView 控制項的項目
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
ms.openlocfilehash: b3cfcc6c2873dfb0eb95cf7950adc6b2bb73e74c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143178"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a><span data-ttu-id="f71a3-102">HOW TO：選取 Windows Forms ListView 控制項的項目</span><span class="sxs-lookup"><span data-stu-id="f71a3-102">How to: Select an Item in the Windows Forms ListView Control</span></span>
<span data-ttu-id="f71a3-103">此範例示範如何以程式設計方式在 Windows Form 中選取的項目<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="f71a3-103">This example demonstrates how to programmatically select an item in a Windows Forms <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="f71a3-104">以程式設計方式選取項目不會自動變更焦點<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="f71a3-104">Selecting an item programmatically does not automatically change the focus to the <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="f71a3-105">基於這個理由，您通常也要設定項目，如已取得焦點時選取項目。</span><span class="sxs-lookup"><span data-stu-id="f71a3-105">For this reason, you will typically also want to set the item as focused when selecting an item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f71a3-106">範例</span><span class="sxs-lookup"><span data-stu-id="f71a3-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f71a3-107">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f71a3-107">Compiling the Code</span></span>  
 <span data-ttu-id="f71a3-108">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f71a3-108">This example requires:</span></span>  
  
-   <span data-ttu-id="f71a3-109">A<xref:System.Windows.Forms.ListView>控制項，名為`listView1`包含至少一個項目。</span><span class="sxs-lookup"><span data-stu-id="f71a3-109">A <xref:System.Windows.Forms.ListView> control named `listView1` that contains at least one item.</span></span>  
  
-   <span data-ttu-id="f71a3-110"><xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="f71a3-110">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71a3-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f71a3-111">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
