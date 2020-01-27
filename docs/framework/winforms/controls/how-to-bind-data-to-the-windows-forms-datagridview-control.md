---
title: 將資料系結至 DataGridView 控制項
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: e2762bf363a469abf8c1e57b851d351c1cb41b62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745084"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>如何：將資料系結至 Windows Forms DataGridView 控制項

<xref:System.Windows.Forms.DataGridView> 控制項支援標準的 Windows Forms 資料系結模型，因此它可以系結至各種不同的資料來源。 通常，您會系結至管理與資料來源互動的 <xref:System.Windows.Forms.BindingSource>。 <xref:System.Windows.Forms.BindingSource> 可以是任何 Windows Forms 的資料來源，讓您在選擇或修改資料的位置時，有很大的彈性。 如需 <xref:System.Windows.Forms.DataGridView> 控制項支援之資料來源的詳細資訊，請參閱[DataGridView 控制項總覽](datagridview-control-overview-windows-forms.md)。  

Visual Studio 對 DataGridView 控制項的資料系結有廣泛的支援。 如需詳細資訊，請參閱[如何：使用設計工具將資料系結至 Windows Forms DataGridView 控制項](bind-data-to-the-datagrid-using-the-designer.md)。  

若要將 DataGridView 控制項連接到資料：

1. 執行方法來處理抓取資料的詳細資訊。 下列程式碼範例會執行初始化 <xref:System.Data.SqlClient.SqlDataAdapter>的 `GetData` 方法，並使用它來填入 <xref:System.Data.DataTable>。 然後，它會將 <xref:System.Data.DataTable> 系結至 <xref:System.Windows.Forms.BindingSource>。 

2. 在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將 <xref:System.Windows.Forms.DataGridView> 控制項系結至 <xref:System.Windows.Forms.BindingSource>，並呼叫 `GetData` 方法來取得資料。  

## <a name="example"></a>範例

這個完整的程式碼範例會從資料庫抓取資料，以在 Windows form 中填入 DataGridView 控制項。 表單也有按鈕可重載資料，並將變更提交至資料庫。  

這個範例需要： 

- Northwind SQL Server 範例資料庫的存取權。 如需有關安裝 Northwind 範例資料庫的詳細資訊，請參閱[取得 ADO.NET 程式碼範例的範例資料庫](../../data/adonet/sql/linq/downloading-sample-databases.md)。 

- 系統、System.web、system.webserver、system.string 和 system.string 元件的參考。  

若要建立並執行此範例，請將程式碼貼入新的 Windows Forms 專案中的*Form1*程式碼檔案。 如需從C#或 Visual Basic 命令列建立的詳細資訊，請參閱[使用 csc 建立命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或[從命令列建立](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
使用 Northwind SQL Server 範例資料庫連接的值填入範例中的 `connectionString` 變數。 Windows 驗證（也稱為整合式安全性）比在連接字串中儲存密碼，是更安全的連接到資料庫的方式。 如需連接安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [保護連接資訊](../../data/adonet/protecting-connection-information.md)
