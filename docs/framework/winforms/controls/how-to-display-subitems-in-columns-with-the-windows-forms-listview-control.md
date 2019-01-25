---
title: HOW TO：使用 Windows Forms ListView 控制項的資料行顯示子項目
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
ms.openlocfilehash: bd41dda048aadc399c7f8ffe0926b010991d08a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686747"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>HOW TO：使用 Windows Forms ListView 控制項的資料行顯示子項目
Windows Form<xref:System.Windows.Forms.ListView>控制項可以顯示額外的文字或詳細資料檢視中的每個項目的子項目。 第一欄會顯示項目文字，例如員工號碼。 第二、 第三和後續的資料行中顯示第一、 第二，以及後續的相關聯的子項目。  
  
### <a name="to-add-subitems-to-a-list-item"></a>若要將子項目加入至清單項目  
  
1.  加入所需的任何資料行。 因為第一欄會顯示項目的<xref:System.Windows.Forms.ListView.Text%2A>屬性，您需要多個資料行多於可用的子項目。 如需有關如何加入資料行的詳細資訊，請參閱[How to:資料行以 Windows Form ListView 控制項中加入](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)。  
  
2.  呼叫<xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A>方法所傳回的集合<xref:System.Windows.Forms.ListViewItem.SubItems%2A>項目的屬性。 下列程式碼範例會設定 employee name 和部門的清單項目。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>另請參閱
- [ListView 控制項概觀](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [如何：新增和移除項目，使用 Windows Forms ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [如何：資料行加入 Windows Form ListView 控制項](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [如何：Windows Form ListView 控制項中顯示的圖示](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [如何：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Form)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
