---
title: 將資料繫結到資料網格視圖控制項
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182268"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>如何：將資料繫結到 Windows 表單資料網格視圖控制項

該<xref:System.Windows.Forms.DataGridView>控制項支援標準 Windows 表單資料繫結模型，因此它可以綁定到各種資料來源。 通常，您將綁定到管理<xref:System.Windows.Forms.BindingSource>與資料來源交互的 。 可以是<xref:System.Windows.Forms.BindingSource>任何 Windows 表單資料來源，這為您提供了在選擇或修改資料位置時的巨大靈活性。 有關<xref:System.Windows.Forms.DataGridView>控制項支援的資料來源的詳細資訊，請參閱[DataGridView 控制項概述](datagridview-control-overview-windows-forms.md)。  

Visual Studio 廣泛支援與 DataGridView 控制項綁定的資料。 有關詳細資訊，請參閱[：使用設計器將資料繫結到 Windows 表單 DataGridView 控制項](bind-data-to-the-datagrid-using-the-designer.md)。  

要將 DataGridView 控制項連接到資料：

1. 實現一種方法來處理檢索資料的詳細資訊。 以下代碼示例實現一個`GetData`方法，該方法初始化<xref:System.Data.SqlClient.SqlDataAdapter>了 ， 並使用它來<xref:System.Data.DataTable>填充 。 然後，它將 綁定<xref:System.Data.DataTable>到<xref:System.Windows.Forms.BindingSource>。

2. 在表單<xref:System.Windows.Forms.Form.Load>的事件處理常式中，將<xref:System.Windows.Forms.DataGridView>控制項綁定到 ，<xref:System.Windows.Forms.BindingSource>並調用`GetData`方法以檢索資料。  

## <a name="example"></a>範例

此完整代碼示例從資料庫中檢索資料以在 Windows 表單中填充 DataGridView 控制項。 該表單還具有重新載入資料和向資料庫提交更改的按鈕。  

這個範例需要：

- 訪問北風 SQL Server 示例資料庫。 有關安裝北風示例資料庫的詳細資訊，請參閱[獲取ADO.NET代碼示例的示例資料庫](../../data/adonet/sql/linq/downloading-sample-databases.md)。

- 對系統、系統.Windows.表單、系統、資料和系統.Xml 程式集的引用。  

要生成和運行此示例，請將代碼粘貼到新 Windows 表單專案中的*Form1*代碼檔中。 有關從 C# 或 Visual Basic 命令列生成的資訊，請參閱[使用 csc.exe 的命令列構建](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[命令列中的生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
使用北`connectionString`風 SQL Server 示例資料庫連接的值填充示例中的變數。 Windows 身份驗證也稱為集成安全，與在連接字串中存儲密碼相比，是連接到資料庫的更安全方法。 有關連接安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [在 Windows 表單資料網格視圖控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [保護連接資訊](../../data/adonet/protecting-connection-information.md)
