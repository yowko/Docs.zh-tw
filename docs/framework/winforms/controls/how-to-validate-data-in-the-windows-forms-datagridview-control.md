---
title: HOW TO：驗證 Windows Forms DataGridView 控制項的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: dae254c14790841b37162fca9f998be429006125
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225608"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a>HOW TO：驗證 Windows Forms DataGridView 控制項的資料
下列程式碼範例示範如何驗證使用者輸入 <xref:System.Windows.Forms.DataGridView> 控制項的資料。 在此範例中，會填入來自 Northwind 範例資料庫 `Customers` 資料表的資料列到 <xref:System.Windows.Forms.DataGridView>。 當使用者編輯 `CompanyName` 資料行中的儲存格時，會檢查是否為空白以測試其值的有效性。 如果 <xref:System.Windows.Forms.DataGridView.CellValidating> 事件的事件處理常式發現此值為空字串，則直到使用者輸入非空白字串之前，<xref:System.Windows.Forms.DataGridView> 會讓使用者不能離開儲存格。  
  
 如需這個程式碼範例的完整說明，請參閱[逐步解說：驗證資料，在 Windows Form DataGridView 控制項](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。   
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [逐步解說：驗證 Windows Form DataGridView 控制項中的資料](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)
