---
title: Windows Form DataGrid 控制項的鍵盤快速鍵
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
ms.openlocfilehash: c05ddd68beeffe70e048a439929fb31454812612
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Windows Form DataGrid 控制項的鍵盤快速鍵
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 下表列出可用於巡覽 Windows 表單中的鍵盤快速鍵<xref:System.Windows.Forms.DataGrid>控制項：  
  
|動作|快速鍵|  
|------------|--------------|  
|完成資料格的項目，並移至下一個儲存格。<br /><br /> 如果焦點是在子資料表連結，請瀏覽至該資料表。|ENTER|  
|如果在資料格的編輯模式，則會取消編輯儲存格。<br /><br /> 如果在點線框選取取消編輯資料列。|ESC|  
|編輯儲存格時，請刪除前插入點的字元。|退格鍵|  
|編輯儲存格時，請在插入點後刪除的字元。|DELETE|  
|移至目前的資料列中的第一個儲存格。|首頁|  
|移到最後一個目前的資料列中的資料格。|END|  
|反白顯示目前儲存格中的字元，並將插入點置於一行的結尾。 相同的行為與按兩下儲存格。|F2|  
|如果焦點是在儲存格上，移至下一個儲存格的資料列中。<br /><br /> 如果焦點是資料列中的最後一個儲存格上，移至 資料列的第一個子資料表連結，然後展開它。<br /><br /> 如果焦點是在子連結，移至下一個子連結。<br /><br /> 如果焦點在最後一個子連結，移至下一個資料列的第一個資料格。|TAB|  
|如果焦點是在儲存格上，移至先前的資料格的資料列中。<br /><br /> 如果焦點是在資料列中的第一個儲存格上，移至先前的資料列的最後一個展開的子資料表連結，或移到最後一個資料格的上一個資料列。<br /><br /> 如果焦點是在子連結，移至前一個子連結。<br /><br /> 如果焦點是在第一個子連結，移至最後一個資料格的上一個資料列。|SHIFT+TAB|  
|移至定位順序中的下一個控制項。|CTRL+TAB|  
|移至定位順序中的上一個控制項。|CTRL+SHIFT+TAB|  
|子資料表中，向上移動以父資料表。 如同按一下 [上一頁] 按鈕的行為相同。|ALT+向左鍵|  
|展開子資料表連結。 ALT + 向下鍵會展開所有連結，而不只是選取的連結。|ALT + 向下鍵或 CTRL + 加號|  
|摺疊子資料表連結。 ALT + 向上鍵可摺疊所有連結，而不只是選取的連結。|ALT + 向上鍵或 CTRL + 減號|  
|移至箭頭的方向遠的非空白儲存格。|CTRL + 方向鍵|  
|延伸選取範圍一個資料列中 （不包括子資料表連結） 箭頭的方向。|SHIFT + 向上/向下鍵|  
|延伸選取範圍中 （不包括子資料表連結） 箭頭的方向遠的非空白資料列。|CTRL + SHIFT + 向上/向下鍵|  
|移至左上資料格。|CTRL + HOME|  
|移至右下資料格。|CTRL + END|  
|延伸選取範圍至上方的資料列。|CTRL + SHIFT + HOME|  
|延伸選取範圍到底部資料列。|CTRL + SHIFT + END|  
|選取目前的資料列 （排除子資料表連結）。|SHIFT + 空格鍵|  
|選取整個方格 （排除子資料表連結）。|CTRL+A|  
|顯示子資料表中的父資料列。|CTRL+PAGE DOWN|  
|隱藏在子資料表中的父資料列。|CTRL+PAGE UP|  
|延伸選取範圍向下移 （排除子資料表連結） 的一個螢幕。|SHIFT+PAGE DOWN|  
|向上延伸選取範圍 （不包括子資料表連結） 的一個螢幕。|SHIFT+PAGE UP|  
|呼叫<xref:System.Windows.Forms.DataGrid.EndEdit%2A>目前資料列的方法。|CTRL+ENTER|  
|輸入<xref:System.DBNull.Value?displayProperty=nameWithType>處於編輯模式時在儲存格中的值。|CTRL+0|  
  
## <a name="see-also"></a>另請參閱  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)
