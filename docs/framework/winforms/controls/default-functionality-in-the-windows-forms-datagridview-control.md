---
title: Windows Form DataGridView 控制項的預設功能
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
ms.openlocfilehash: 26633b0abaa8c1c2916153b2236ecf9e4982fd68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208861"
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a>Windows Form DataGridView 控制項的預設功能
Windows Form<xref:System.Windows.Forms.DataGridView>控制項提供使用者一段很長的預設功能。  
  
## <a name="default-functionality"></a>預設功能  
 根據預設，<xref:System.Windows.Forms.DataGridView>控制項：  
  
-   會自動顯示資料行標頭和保持可見的因為資料表垂直捲動的資料列行首。  
  
-   有資料列標頭，其中包含目前資料列選取範圍指標。  
  
-   第一個資料格中有選取矩形。  
  
-   有可以使用者按兩下資料行分隔線時，自動調整大小的資料行。  
  
-   會自動在 Windows XP 和 Windows Server 2003 系列支援視覺化樣式時<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法從應用程式的呼叫`Main`方法。  
  
 此外，內容<xref:System.Windows.Forms.DataGridView>控制項可以編輯預設值：  
  
-   如果使用者按兩下，或按下 f2 鍵在資料格中，控制項將會自動將儲存格進入編輯模式並更新資料格內容，當使用者輸入。  
  
-   如果使用者捲動至方格的結尾時，使用者會看到加入新資料錄的資料列會出現。 當使用者按一下此資料列時，要將新的資料列加入至<xref:System.Windows.Forms.DataGridView>控制，使用預設值。 當使用者按下 esc 鍵時，這個新的資料列就會消失。  
  
-   如果使用者按一下資料列行首時，會選取整個資料列。  
  
 當您繫結<xref:System.Windows.Forms.DataGridView>藉由設定資料來源的控制項及其<xref:System.Windows.Forms.DataGridView.DataSource%2A>屬性、 控制項：  
  
-   會自動為資料行標頭文字中使用資料來源的資料行的名稱。  
  
-   填入資料來源的內容。 <xref:System.Windows.Forms.DataGridView> 每個資料行的資料來源中，會自動建立資料行。  
  
-   建立資料表中的每個可見的資料列的資料列。  
  
-   自動排序依據的基礎資料，當使用者按一下資料行標頭的資料列。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView 控制項](datagridview-control-windows-forms.md)
