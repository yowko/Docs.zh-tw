---
title: Windows Form DataGrid 控制項的鍵盤快速鍵
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
ms.openlocfilehash: c04340cf2d2c8e318ea7348c978ef943563c24da
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711768"
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Windows Form DataGrid 控制項的鍵盤快速鍵
> [!NOTE]
>  
  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。 如需詳細資訊，請參閱 [Windows Forms DataGridView 和 DataGrid 控制項之間的差異](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 下表列出可用於巡覽 Windows 表單中的鍵盤快速鍵<xref:System.Windows.Forms.DataGrid>控制項：  
  
|動作|快速鍵|  
|------------|--------------|  
|完成的資料格的項目，並向下移至下一個儲存格。<br /><br /> 如果焦點是在子資料表連結，瀏覽至該資料表。|ENTER|  
|如果在 儲存格編輯模式中，則會取消儲存格編輯。<br /><br /> 在點線框選取項目，如果會取消資料列上編輯。|ESC|  
|編輯儲存格時，請刪除插入點之前的字元。|退格鍵|  
|編輯儲存格時，會在插入點後刪除的字元。|DELETE|  
|移至目前的資料列的第一個儲存格。|首頁|  
|移至最後一個目前的資料列中的資料格。|END|  
|反白顯示目前儲存格中的字元，並放在該行結尾的插入點。 與按兩下儲存格有相同的行為。|F2|  
|如果焦點是在儲存格上，移至下一個儲存格的資料列中。<br /><br /> 如果焦點是在資料列中最後一個儲存格上，移至 資料列的第一個子資料表連結並將其展開。<br /><br /> 如果焦點是子系 連結，移至下一步 的 子系 連結。<br /><br /> 如果焦點是最後一個子系連結，移至下一個資料列的第一個資料格。|TAB|  
|如果焦點是在儲存格上，移至先前的儲存格中的資料列中。<br /><br /> 如果焦點是資料列中的第一個儲存格上，移至先前的資料列的最後一個擴充的子資料表連結，或移到最後一個資料格前一個資料列。<br /><br /> 如果焦點是子系 連結，移至前一個子連結。<br /><br /> 如果焦點是在第一個子連結，移到最後的前一個資料列的資料格。|SHIFT+TAB|  
|移至定位順序中的下一個控制項。|CTRL+TAB|  
|移至定位順序中的前一個控制項。|CTRL+SHIFT+TAB|  
|子資料表中，移至父資料表。 與按一下 [上一頁] 按鈕的行為相同。|ALT+向左鍵|  
|展開子資料表的連結。 ALT + 向下箭號展開所有連結，而不只是選取的連結。|ALT + 向下鍵或 CTRL + 加號|  
|摺疊子資料表的連結。 ALT + 向上鍵摺疊所有連結，而不只是選取的連結。|ALT + 向上鍵或 CTRL + 減號|  
|移至的箭頭方向遠的非空白儲存格。|CTRL + 方向鍵|  
|延伸選取範圍中的資料列的方向 （不包括子資料表連結） 的箭號。|SHIFT + 向上/向下箭號|  
|延伸選取範圍 （不包括子資料表連結） 的箭頭方向中的最遠的非空白資料列。|CTRL + SHIFT + 向上/向下鍵|  
|移至左上方儲存格。|CTRL + HOME|  
|移至右下方儲存格中。|CTRL + END|  
|延伸選取範圍到上方的資料列。|CTRL + SHIFT + HOME|  
|延伸選取範圍到下方的資料列。|CTRL + SHIFT + END|  
|選取目前的資料列 （不包括子資料表連結）。|SHIFT + 空格鍵|  
|選取整個方格 （不包括子資料表連結）。|CTRL+A|  
|顯示子資料表中的父資料列。|CTRL+PAGE DOWN|  
|隱藏在子資料表中的父資料列。|CTRL+PAGE UP|  
|延伸選取範圍向下一個畫面 （不包括子資料表連結）。|SHIFT+PAGE DOWN|  
|向上延伸選取範圍 （不包括子資料表連結） 的其中一個畫面。|SHIFT+PAGE UP|  
|呼叫<xref:System.Windows.Forms.DataGrid.EndEdit%2A>目前資料列的方法。|CTRL+ENTER|  
|輸入<xref:System.DBNull.Value?displayProperty=nameWithType>在編輯模式中的儲存格中的值。|CTRL+0|  
  
## <a name="see-also"></a>另請參閱
- [DataGrid 控制項概觀](datagrid-control-overview-windows-forms.md)
- [DataGrid 控制項](datagrid-control-windows-forms.md)
