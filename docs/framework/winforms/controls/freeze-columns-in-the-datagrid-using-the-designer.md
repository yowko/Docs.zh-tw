---
title: 如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: 3da253369cc70c7757f0119c03012d9d8591d6da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用設計工具凍結 Windows Form DataGridView 控制項中的資料行
當使用者檢視顯示於 Windows Form <xref:System.Windows.Forms.DataGridView> 控制項的資料時，有時候需要經常參考單一資料行或資料行集合。 比方說，當您顯示包含許多資料行的客戶資訊的資料表，它可用於其他資料行可在可見區域外捲動仍一直顯示客戶的名稱。  
  
 若要達到這種行為，您可以凍結控制項中的資料行。 當您凍結資料行時，也會凍結在該資料行左邊的所有資料行 (如果是從右至左的字集，則會凍結右邊的所有資料行)。 凍結的資料行會留在原處，而其他所有資料行則可以捲動。 如果啟用了資料行重新調整順序，則會將凍結的資料行視為與未凍結的資料行有所區別的群組。 使用者可以在任一群組中重新調整資料行位置，但無法將資料行從一個群組移至另一個。  
  
 下列程序需要**Windows 應用程式**表單，其中包含與專案<xref:System.Windows.Forms.DataGridView>控制項。 設定這類專案的詳細資訊，請參閱[How to： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[How to： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-freeze-a-column-using-the-designer"></a>若要凍結資料行使用設計工具  
  
1.  按一下智慧標籤圖像 (![智慧標籤圖像](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) 上的右上角<xref:System.Windows.Forms.DataGridView>控制項，然後再選取**編輯資料行**。  
  
2.  選取的資料行**選取的資料行**清單。  
  
3.  在**資料行屬性**方格中，設定<xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A>屬性`true`。  
  
    > [!NOTE]
    >  您也可以凍結資料行資料時將它加入選取**Frozen**方塊中**加入資料行** 對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 [操作說明：使用設計工具在 Windows Forms DataGridView 控制項中新增和移除資料行](../../../../docs/framework/winforms/controls/add-and-remove-columns-in-the-datagrid-using-the-designer.md)  
 [操作說明：使用設計工具在 Windows Forms DataGridView 控制項中啟用資料行重新調整順序](../../../../docs/framework/winforms/controls/enable-column-reordering-in-the-datagrid-using-the-designer.md)  
 [如何： 顯示 Windows Form 全球化由右至左文字](http://msdn.microsoft.com/library/f0663385-2354-4c65-8676-706422283b14)  
 [如何： 建立 Windows 應用程式專案](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [操作說明：將控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
