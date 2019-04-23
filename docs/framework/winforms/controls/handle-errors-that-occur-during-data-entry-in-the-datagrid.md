---
title: HOW TO：處理 Windows Forms DataGridView 控制項在資料輸入期間發生的錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: e5ba42c2ff86f46e2722d0f4455c10ab7b85af1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204649"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>HOW TO：處理 Windows Forms DataGridView 控制項在資料輸入期間發生的錯誤
下列程式碼範例示範如何使用 <xref:System.Windows.Forms.DataGridView> 控制項，將資料輸入錯誤回報給使用者。  
  
 如需這個程式碼範例的完整說明，請參閱[逐步解說：處理在 Windows 中的資料輸入期間所發生的錯誤 Form DataGridView 控制項](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Windows.Forms 和 System.XML 組件的參考。   
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../data/adonet/protecting-connection-information.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [逐步解說：處理 Windows Form DataGridView 控制項中的資料輸入期間所發生的錯誤](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Windows Forms DataGridView 控制項中的資料輸入](data-entry-in-the-windows-forms-datagridview-control.md)
- [逐步解說：驗證 Windows Form DataGridView 控制項中的資料](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [保護連線資訊](../../data/adonet/protecting-connection-information.md)
