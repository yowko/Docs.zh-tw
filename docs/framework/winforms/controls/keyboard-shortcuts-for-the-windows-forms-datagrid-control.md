---
title: Windows Form DataGrid 控制項的鍵盤快速鍵
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
ms.openlocfilehash: 6b4d566d377a3cda73bf8422caa798134d356f63
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962575"
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Windows Form DataGrid 控制項的鍵盤快速鍵
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 下表列出可用於 Windows Forms <xref:System.Windows.Forms.DataGrid>控制項內導覽的鍵盤快速鍵:  
  
|動作|快速鍵|  
|------------|--------------|  
|完成儲存格專案, 並向下移動至下一個儲存格。<br /><br /> 如果焦點是在子資料工作表連結上, 請流覽至該資料表。|ENTER|  
|如果在儲存格編輯模式中, 則取消儲存格編輯。<br /><br /> 如果在字幕選取範圍中, 取消資料列的編輯。|ESC|  
|在編輯儲存格時, 刪除插入點之前的字元。|倒退鍵|  
|編輯資料格時, 刪除插入點之後的字元。|Delete|  
|移至目前資料列中的第一個資料格。|首頁|  
|移至目前資料列中的最後一個資料格。|END|  
|反白顯示目前儲存格中的字元, 並將插入點放在行尾。 與按兩下資料格的行為相同。|F2|  
|如果焦點是在資料格上, 請移至資料列中的下一個儲存格。<br /><br /> 如果焦點是在資料列中的最後一個資料格上, 請移至資料列的第一個子資料工作表連結, 然後將它展開。<br /><br /> 如果焦點是在子連結上, 請移至下一個子連結。<br /><br /> 如果焦點是在最後一個子連結上, 請移至下一個資料列的第一個資料格。|TAB|  
|如果焦點是在資料格上, 請移至資料列中的上一個儲存格。<br /><br /> 如果焦點是在資料列中的第一個資料格上, 請移至前一個資料列的最後一個展開的子資料工作表連結, 或移至前一個資料列的最後一個資料格。<br /><br /> 如果焦點是在子連結上, 請移至上一個子連結。<br /><br /> 如果焦點是在第一個子系連結上, 請移至上一個資料列的最後一個資料格。|SHIFT+TAB|  
|移至定位順序中的下一個控制項。|CTRL+TAB|  
|移至定位順序中的上一個控制項。|CTRL+SHIFT+TAB|  
|如果在子資料工作表中, 則移到父資料表。 與按一下 [上一頁] 按鈕的行為相同。|ALT+向左鍵|  
|展開 [子資料工作表連結]。 ALT + 向下鍵會展開所有的連結, 而不只是選取的連結。|ALT + 向下鍵或 CTRL + 加號|  
|折迭子資料工作表連結。 ALT + 向上鍵會折迭所有的連結, 而不只是選取的連結。|ALT + 向上鍵或 CTRL + 減號|  
|移至箭號方向的最遠非空白儲存格。|CTRL + 箭號|  
|以箭號的方向, 將選取範圍延伸一個資料列 (不包括子資料工作表連結)。|SHIFT + 向上鍵/向下鍵|  
|以箭號的方向, 將選取範圍擴充到最遠的非空白資料列 (不包括子資料工作表連結)。|CTRL + SHIFT + 向上/向下鍵|  
|移至左上方資料格。|CTRL + HOME|  
|移至右下方的資料格。|CTRL + END|  
|將選取範圍延伸到頂端資料列。|CTRL + SHIFT + HOME|  
|將選取範圍延伸至底部資料列。|CTRL + SHIFT + END|  
|選取目前的資料列 (不包括子資料工作表連結)。|SHIFT + 空格鍵|  
|選取整個方格 (不包括子資料工作表連結)。|CTRL+A|  
|在子資料工作表中顯示父資料列。|CTRL+PAGE DOWN|  
|在子資料工作表中隱藏父資料列。|CTRL+PAGE UP|  
|將選取範圍向下延伸一個畫面 (不包括子資料工作表連結)。|SHIFT+PAGE DOWN|  
|將選取範圍向上延伸一個畫面 (不包括子資料工作表連結)。|SHIFT+PAGE UP|  
|呼叫目前<xref:System.Windows.Forms.DataGrid.EndEdit%2A>資料列的方法。|CTRL+ENTER|  
|當處於編輯模式時, 將值輸入儲存格。<xref:System.DBNull.Value?displayProperty=nameWithType>|CTRL+0|  
  
## <a name="see-also"></a>另請參閱

- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
