---
title: 將資料行新增至 ListView 控制項
description: 瞭解如何將資料行新增至 Windows Forms ListView 控制項，以顯示每個清單專案的數種類型資訊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
- list views [Windows Forms], adding columns
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
ms.openlocfilehash: 7ca4e86ca3a9679876f2525c49596534f175096a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174558"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control"></a>如何：將資料行加入至 Windows Form ListView 控制項
在詳細資料檢視中， <xref:System.Windows.Forms.ListView> 控制項可以顯示每個清單專案的多個資料行。 您可以使用資料行向使用者顯示每個清單專案的數種類型資訊。 例如，檔案清單可以顯示檔案上次修改的檔案名、檔案類型、大小和日期。 如需建立資料行之後將其填入的詳細資訊，請參閱[如何：在具有 Windows Forms ListView 控制項的資料行中顯示](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)子工作。  
  
### <a name="to-add-columns-programmatically"></a>以程式設計方式新增資料行  
  
1. 將控制項的 <xref:System.Windows.Forms.ListView.View%2A> 屬性設為 <xref:System.Windows.Forms.View.Details> 。  
  
2. 使用 <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> 清單視圖的屬性的方法 <xref:System.Windows.Forms.ListView.Columns%2A> 。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ListView>
- [ListView 控制項](listview-control-windows-forms.md)
- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
