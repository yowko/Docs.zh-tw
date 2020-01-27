---
title: DataGridView 控制項中的預設功能
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: b695883ac7ec3fb0c459adb66214b0eceab3a128
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746128"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項的預設功能
Windows Forms <xref:System.Windows.Forms.DataGridView> 控制項提供大量的預設功能給使用者。  
  
## <a name="default-functionality"></a>預設功能  
 根據預設，<xref:System.Windows.Forms.DataGridView> 控制項：  
  
- 當資料表垂直捲動時，自動顯示資料行標頭和資料列標頭保持可見。  
  
- 具有資料列標頭，其中包含目前資料列的選取範圍指示器。  
  
- 在第一個資料格中有一個選取矩形。  
  
- 具有可在使用者按兩下資料行分隔線時自動調整大小的資料行。  
  
- 從應用程式的 `Main` 方法呼叫 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> 方法時，會自動支援 Windows XP 和 Windows Server 2003 系列的視覺化樣式。  
  
 此外，預設可以編輯 <xref:System.Windows.Forms.DataGridView> 控制項的內容：  
  
- 如果使用者按兩下或按下儲存格的 F2，控制項會自動將儲存格置於編輯模式，並將資料格的內容更新為使用者類型。  
  
- 如果使用者滾動到方格的結尾，則使用者會看到加入新記錄的資料列存在。 當使用者按一下此資料列時，新的資料列就會加入至 <xref:System.Windows.Forms.DataGridView> 控制項，其中包含預設值。 當使用者按下 ESC 鍵時，這個新的資料列就會消失。  
  
- 如果使用者按一下資料列標頭，則會選取整個資料列。  
  
 當您藉由設定 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 屬性，將 <xref:System.Windows.Forms.DataGridView> 控制項系結至資料來源時，控制項會：  
  
- 會自動使用資料來源的資料行名稱做為欄標題文字。  
  
- 會填入資料來源的內容。 系統會針對資料來源中的每個資料行自動建立 <xref:System.Windows.Forms.DataGridView> 資料行。  
  
- 針對資料表中的每個可見資料列建立一個資料列。  
  
- 當使用者按一下資料行標頭時，會自動根據基礎資料排序資料列。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView 控制項](datagridview-control-windows-forms.md)
