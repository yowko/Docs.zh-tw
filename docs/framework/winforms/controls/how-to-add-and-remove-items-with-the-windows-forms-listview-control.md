---
title: "如何：使用 Windows Form ListView 控制項加入和移除項目"
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
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b7c9d92e4ba58ae5c5f2cbff1c79fd7a3ae673a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a><span data-ttu-id="aa108-102">如何：使用 Windows Form ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="aa108-102">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>
<span data-ttu-id="aa108-103">加入 Windows Form 中的項目中的程序<xref:System.Windows.Forms.ListView>控制項包含主要是指定的項目，並將內容指派給它。</span><span class="sxs-lookup"><span data-stu-id="aa108-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="aa108-104">新增或移除清單項目即可在任何時間。</span><span class="sxs-lookup"><span data-stu-id="aa108-104">Adding or removing list items can be done at any time.</span></span>  
  
### <a name="to-add-items-programmatically"></a><span data-ttu-id="aa108-105">以程式設計方式將項目</span><span class="sxs-lookup"><span data-stu-id="aa108-105">To add items programmatically</span></span>  
  
1.  <span data-ttu-id="aa108-106">使用<xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A>方法<xref:System.Windows.Forms.ListView.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="aa108-106">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a><span data-ttu-id="aa108-107">若要以程式設計方式移除項目</span><span class="sxs-lookup"><span data-stu-id="aa108-107">To remove items programmatically</span></span>  
  
1.  <span data-ttu-id="aa108-108">使用<xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>或<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A>方法<xref:System.Windows.Forms.ListView.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="aa108-108">Use the <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> or <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method of the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span> <span data-ttu-id="aa108-109"><xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>方法移除單一項目;<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A>方法從清單中移除所有項目。</span><span class="sxs-lookup"><span data-stu-id="aa108-109">The <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> method removes a single item; the <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> method removes all items from the list.</span></span>  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="aa108-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa108-110">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 [<span data-ttu-id="aa108-111">ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="aa108-111">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="aa108-112">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="aa108-112">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
