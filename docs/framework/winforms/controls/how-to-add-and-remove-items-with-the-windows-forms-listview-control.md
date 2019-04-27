---
title: HOW TO：使用 Windows Forms ListView 控制項新增和移除項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: 8a97d73b9b2c46d02ae0794ad66b20a04db58af6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011121"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="b4b55-102">HOW TO：使用 Windows Forms ListView 控制項新增和移除項目</span><span class="sxs-lookup"><span data-stu-id="b4b55-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="b4b55-103">加入 Windows Form 中的項目中的程序<xref:System.Windows.Forms.ListView>控制主要包含指定的項目，並將屬性指派給它。</span><span class="sxs-lookup"><span data-stu-id="b4b55-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="b4b55-104">隨時都可以新增或移除清單項目。</span><span class="sxs-lookup"><span data-stu-id="b4b55-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="b4b55-105">以程式設計方式將項目</span><span class="sxs-lookup"><span data-stu-id="b4b55-105">To add items programmatically</span></span>  
  
1. <span data-ttu-id="b4b55-106">使用<xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A>方法的<xref:System.Windows.Forms.ListView.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b4b55-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="b4b55-107">若要以程式設計方式移除項目</span><span class="sxs-lookup"><span data-stu-id="b4b55-107">To remove items programmatically</span></span>  
  
1. <span data-ttu-id="b4b55-108">使用<xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>或是<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A>方法<xref:System.Windows.Forms.ListView.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b4b55-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="b4b55-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>方法會移除單一項目;<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A>方法從清單中移除所有項目。</span><span class="sxs-lookup"><span data-stu-id="b4b55-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="b4b55-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4b55-110">See also</span></span>

- <xref:System.Windows.Forms.ListView>
- [<span data-ttu-id="b4b55-111">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="b4b55-111">ListView Control</span></span>](listview-control-windows-forms.md)
- [<span data-ttu-id="b4b55-112">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b4b55-112">ListView Control Overview</span></span>](listview-control-overview-windows-forms.md)
