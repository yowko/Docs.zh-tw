---
title: 顯示 ListView 控制項的圖示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 5fc54c448dae95cab50cdafa8403769fb421dffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744500"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>如何：顯示 Windows Form ListView 控制項的圖示
Windows Forms <xref:System.Windows.Forms.ListView> 控制項可以顯示三個影像清單中的圖示。 [清單]、[詳細資料] 和 [SmallIcon] 視圖會顯示 [<xref:System.Windows.Forms.ListView.SmallImageList%2A>] 屬性中所指定影像清單中的影像。 [LargeIcon] 視圖會顯示 [<xref:System.Windows.Forms.ListView.LargeImageList%2A>] 屬性中所指定影像清單中的影像。 清單視圖也可以在 [<xref:System.Windows.Forms.ListView.StateImageList%2A>] 屬性中，于大型或小圖示旁顯示一組額外的圖示。 如需影像清單的詳細資訊，請參閱[ImageList 元件](imagelist-component-windows-forms.md)和[如何：使用 Windows Forms ImageList 元件來新增或移除影像](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)。  
  
### <a name="to-display-images-in-a-list-view"></a>若要在清單視圖中顯示影像  
  
1. 將適當的屬性（<xref:System.Windows.Forms.ListView.SmallImageList%2A>、<xref:System.Windows.Forms.ListView.LargeImageList%2A>或 <xref:System.Windows.Forms.ListView.StateImageList%2A>）設定為您想要使用的現有 <xref:System.Windows.Forms.ImageList> 元件。  
  
     這些屬性可以在設計工具中，使用屬性視窗或程式碼來設定。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. 針對具有相關聯圖示的每個清單專案，設定 [<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>] 或 [<xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A>] 屬性。  
  
     這些屬性可以在程式碼中設定，或在 [ **ListViewItem 集合編輯器**] 內設定。 若要開啟 [ **ListViewItem 集合編輯器**]，請按一下省略號按鈕（![[**屬性**] 視窗上 [<xref:System.Windows.Forms.ListView.Items%2A>] 屬性旁邊的 Visual Studio.](./media/visual-studio-ellipsis-button.png)）屬性視窗中的省略號按鈕（...）。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>請參閱

- [ListView 控制項概觀](listview-control-overview-windows-forms.md)
- [操作說明：使用 Windows Forms ListView 控制項加入和移除項目](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [操作說明：將資料行加入至 Windows Forms ListView 控制項](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [ImageList 元件](imagelist-component-windows-forms.md)
