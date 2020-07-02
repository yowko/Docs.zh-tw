---
title: 使用 ListView 控制項新增和移除專案
description: 瞭解如何藉由指定專案並為其指派屬性，來新增和移除具有 Windows Forms ListView 控制項的專案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], populating
- list views [Windows Forms], adding list items
- ListView control [Windows Forms], adding list items
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
ms.openlocfilehash: db374ded69bcbd93527381d75a8ff751a1c9abe6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618086"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control"></a>如何：使用 Windows Form ListView 控制項加入和移除項目
將專案加入至 Windows Forms 控制項的程式 <xref:System.Windows.Forms.ListView> 主要是由指定專案並指派屬性給它。 您可以隨時完成新增或移除清單專案。  
  
### <a name="to-add-items-programmatically"></a>以程式設計方式新增專案  
  
1. 使用 <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> 屬性的方法 <xref:System.Windows.Forms.ListView.Items%2A> 。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### <a name="to-remove-items-programmatically"></a>以程式設計方式移除專案  
  
1. 使用 <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> 屬性的或 <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> 方法 <xref:System.Windows.Forms.ListView.Items%2A> 。 <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A>方法會移除單一專案，方法會 <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> 從清單中移除所有專案。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- [ListView 控制項](listview-control-windows-forms.md)
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
