---
title: 在具有 ListView 控制項的資料行中顯示子項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: 5c6d807410ad4ee0198d6334844bd65b148edff4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745540"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>如何：使用 Windows Form ListView 控制項以資料行顯示子項目
Windows Forms <xref:System.Windows.Forms.ListView> 控制項可以針對詳細資料檢視中的每個專案顯示額外的文字或子專案。 第一個資料行顯示專案文字，例如員工編號。 第二、第三和後續的資料行顯示第一個、第二個和後續相關聯的子工作。  
  
### <a name="to-add-subitems-to-a-list-item"></a>將子專案加入至清單專案  
  
1. 加入所需的任何資料行。 因為第一個資料行會顯示專案的 <xref:System.Windows.Forms.ListView.Text%2A> 屬性，所以您所需的資料行比子專案多一個。 如需新增資料行的詳細資訊，請參閱[如何：將資料行加入至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)。  
  
2. 呼叫專案的 <xref:System.Windows.Forms.ListViewItem.SubItems%2A> 屬性所傳回之集合的 <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> 方法。 下列程式碼範例會設定清單專案的員工名稱和部門。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>另請參閱

- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [操作說明：將資料行加入至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [操作說明：顯示 Windows Forms ListView 控制項的圖示](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
