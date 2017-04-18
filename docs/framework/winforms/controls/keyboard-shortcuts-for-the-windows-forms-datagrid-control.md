---
title: "Windows Form DataGrid 控制項的鍵盤快速鍵 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DataGrid 控制項 [Windows Form], 巡覽鍵"
  - "鍵盤快速鍵, DataGrid 控制項"
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows Form DataGrid 控制項的鍵盤快速鍵
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控制項會取代 <xref:System.Windows.Forms.DataGrid> 控制項並加入其他功能，不過您也可以選擇保留 <xref:System.Windows.Forms.DataGrid> 控制項，以提供回溯相容性及未來使用。  如需詳細資訊，請參閱 [Windows Form DataGridView 和 DataGrid 控制項之間的差異](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 下列資料表將列出可用來在 Windows Form <xref:System.Windows.Forms.DataGrid> 控制項內巡覽的鍵盤快速鍵：  
  
|動作|快速鍵|  
|--------|---------|  
|完成儲存格輸入並移至下一個儲存格。<br /><br /> 如果焦點 \(Focus\) 在子資料表連結上，則會巡覽至該資料表。|ENTER|  
|如果在儲存格編輯模式中，會取消儲存格編輯。<br /><br /> 如果在跑馬燈選取中，則會取消資料列上的編輯。|ESC|  
|當編輯儲存格時刪除插入點前的字元。|退格鍵|  
|當編輯儲存格時刪除插入點後的字元。|DELETE|  
|移至目前資料列的第一個儲存格。|HOME|  
|移至目前資料列的最後一個儲存格。|END|  
|反白顯示目前儲存格中的字元並將插入點置於行尾。  行為與按兩下儲存格相同。|F2|  
|如果焦點在儲存格上，則會移至資料列的下一個儲存格。<br /><br /> 如果焦點在資料列的最後一個儲存格上，則會移至資料列的第一個子資料表連結並展開它。<br /><br /> 如果焦點在子資料表連結上，則會移至下一個子連結。<br /><br /> 如果焦點在最後一個子連結上，則會移至下一個資料列的第一個儲存格。|TAB|  
|如果焦點在儲存格上，則會移至資料列的上一個儲存格。<br /><br /> 如果焦點在資料列的第一個儲存格上，則會移至上一個資料列的最後一個展開的子資料表連結，或是移至上一個資料列的最後一個儲存格。<br /><br /> 如果焦點在子資料表連結上，則會移至上一個子連結。<br /><br /> 如果焦點在第一個子連結上，則會移至上一個資料列的最後一個儲存格。|SHIFT\+TAB|  
|依定位順序移至下一個控制項。|CTRL\+TAB|  
|依定位順序移至上一個控制項。|CTRL\+SHIFT\+TAB|  
|如果在子資料表中，就會上移至父資料表。  行為與按一下 \[上一步\] 按鈕相同。|ALT\+ 向左鍵|  
|展開子資料表連結。  ALT\+ 向下鍵會展開所有連結，而不只是選取的連結。|ALT\+ 向下鍵或 CTRL\+ 加號|  
|摺疊子資料表連結。  ALT\+ 向上鍵會摺疊所有連結，而不只是選取的連結。|ALT\+ 向上鍵或 CTRL\+ 減號|  
|依箭號方向移至最遠的非空白儲存格。|CTRL\+ARROW|  
|依箭頭方向將選取擴充一個資料列 \(不包含子資料表連結\)。|SHIFT\+ 向上\/向下鍵|  
|依箭頭方向將選取擴充至最遠的非空白資料列 \(不包含子資料表連結\)。|CTRL\+SHIFT\+ 向上\/向下鍵|  
|移至最左上角的儲存格。|CTRL\+HOME|  
|移至最右下角的儲存格。|CTRL\+END|  
|將選取擴充至頂端列。|CTRL\+SHIFT\+HOME|  
|將選取擴充至底端列。|CTRL\+SHIFT\+END|  
|選取目前資料列 \(不包含子資料表連結\)。|SHIFT\+ 空格鍵|  
|選取整個方格 \(不包含子資料表連結\)。|CTRL\+A|  
|當在子資料表時顯示父資料列。|CTRL\+PAGE DOWN|  
|當在子資料表時隱藏父資料列。|CTRL\+PAGE UP|  
|將選取往螢幕下方擴充 \(不包含子資料表連結\)。|SHIFT\+PAGE DOWN|  
|將選取往螢幕上方擴充 \(不包含子資料表連結\)。|SHIFT\+PAGE UP|  
|呼叫目前資料列的 <xref:System.Windows.Forms.DataGrid.EndEdit%2A> 方法。|CTRL\+ENTER|  
|當處於編輯模式時將 <xref:System.DBNull.Value?displayProperty=fullName> 值輸入儲存格中。|CTRL\+0|  
  
## 請參閱  
 [DataGrid 控制項概觀](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)   
 [DataGrid 控制項](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)