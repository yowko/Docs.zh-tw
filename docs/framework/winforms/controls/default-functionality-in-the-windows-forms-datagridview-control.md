---
title: Windows Form DataGridView 控制項的預設功能
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: a475d8bce388860c88571fbf638d206bfe01223d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項的預設功能
Windows Form<xref:System.Windows.Forms.DataGridView>控制為使用者提供相當大的預設功能。  
  
## <a name="default-functionality"></a>預設功能  
 根據預設，<xref:System.Windows.Forms.DataGridView>控制項：  
  
-   會自動顯示資料行標頭和表格垂直捲動時保持可見的資料列標頭。  
  
-   有資料列標題，其中包含目前資料列之選取項目指標。  
  
-   已選取矩形中第一個資料格。  
  
-   有使用者按兩下資料行分隔線時要自動調整的資料行。  
  
-   會自動在 Windows XP 和 Windows Server 2003 系列上支援視覺化樣式時<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法從應用程式的呼叫`Main`方法。  
  
 此外，內容<xref:System.Windows.Forms.DataGridView>控制項可以編輯預設值：  
  
-   如果使用者按兩下，或按 F2，在資料格中，控制項自動儲存格置於編輯模式，並更新資料格內容，做為使用者型別。  
  
-   如果使用者捲動至方格的結尾，使用者會看到加入新資料錄的資料列，會顯示。 當使用者按一下此資料列時，加入新的資料列<xref:System.Windows.Forms.DataGridView>控制項，使用預設值。 當使用者按下 esc 鍵時，這個新的資料列就會消失。  
  
-   如果使用者按一下資料列標頭時，會選取整個資料列。  
  
 當您繫結<xref:System.Windows.Forms.DataGridView>控制項至資料來源，藉由設定其<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性、 控制項：  
  
-   會自動使用資料來源的資料行名稱做為資料行標頭文字。  
  
-   填入資料來源的內容。 <xref:System.Windows.Forms.DataGridView> 每個資料行的資料來源中，會自動建立資料行。  
  
-   在資料表中建立每個可見資料列的資料列。  
  
-   自動排序依據基礎資料，當使用者按一下資料行標頭的資料列。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 [DataGridView 控制項](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
