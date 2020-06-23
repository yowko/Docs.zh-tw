---
title: 將資料系結至 DataGridView 控制項
ms.date: 02/08/2019
description: 瞭解 DataGridView 控制項如何支援標準 Windows Forms 資料系結模型，使其可以系結至各種不同的資料來源。
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904412"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>如何：將資料系結至 Windows Forms DataGridView 控制項

<xref:System.Windows.Forms.DataGridView>控制項支援標準 Windows Forms 資料系結模型，因此可以系結至各種不同的資料來源。 通常，您會系結至 <xref:System.Windows.Forms.BindingSource> 管理與資料來源互動的。 <xref:System.Windows.Forms.BindingSource>可以是任何 Windows Forms 的資料來源，讓您在選擇或修改資料的位置時，有很大的彈性。 如需控制項支援之資料來源的詳細資訊 <xref:System.Windows.Forms.DataGridView> ，請參閱[DataGridView 控制項總覽](datagridview-control-overview-windows-forms.md)。  

Visual Studio 對 DataGridView 控制項的資料系結有廣泛的支援。 如需詳細資訊，請參閱[如何：使用設計工具將資料系結至 Windows Forms DataGridView 控制項](bind-data-to-the-datagrid-using-the-designer.md)。  

若要將 DataGridView 控制項連接到資料：

1. 執行方法來處理抓取資料的詳細資訊。 下列程式碼範例會執行 `GetData` 初始化的方法， <xref:System.Data.SqlClient.SqlDataAdapter> 並使用它來填入 <xref:System.Data.DataTable> 。 然後，它會將系結 <xref:System.Data.DataTable> 至 <xref:System.Windows.Forms.BindingSource> 。

2. 在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將控制項系結 <xref:System.Windows.Forms.DataGridView> 至 <xref:System.Windows.Forms.BindingSource> ，並呼叫 `GetData` 方法來取得資料。  

## <a name="example"></a>範例

這個完整的程式碼範例會從資料庫抓取資料，以在 Windows form 中填入 DataGridView 控制項。 表單也有按鈕可重載資料，並將變更提交至資料庫。  

這個範例需要：

- Northwind SQL Server 範例資料庫的存取權。 如需有關安裝 Northwind 範例資料庫的詳細資訊，請參閱[取得 ADO.NET 程式碼範例的範例資料庫](../../data/adonet/sql/linq/downloading-sample-databases.md)。

- 系統、System.web、System.web 和 System.Xml 元件的參考。  

若要建立並執行此範例，請將程式碼貼入新的 Windows Forms 專案中的*Form1*程式碼檔案。 如需從 c # 或 Visual Basic 命令列建立的詳細資訊，請參閱[使用 csc.exe的命令列建立](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建立](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
`connectionString`使用 Northwind SQL Server 範例資料庫連接的值，在範例中填入變數。 Windows 驗證（也稱為整合式安全性）比在連接字串中儲存密碼，是更安全的連接到資料庫的方式。 如需連接安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [保護連接資訊](../../data/adonet/protecting-connection-information.md)
