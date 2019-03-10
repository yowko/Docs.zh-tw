---
title: HOW TO：將資料繫結至 Windows Form DataGridView 控制項
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcc04625a14ebc23cacfb567951bf8f76f14985
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725099"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>HOW TO：將資料繫結至 Windows Form DataGridView 控制項

<xref:System.Windows.Forms.DataGridView>控制項支援標準的 Windows Form 資料繫結模型，因此它可以繫結至各種資料來源。 通常，您將繫結至<xref:System.Windows.Forms.BindingSource>管理與資料來源互動。 <xref:System.Windows.Forms.BindingSource>可以是任何 Windows Form 資料來源，可讓您更彈性地選擇或修改您的資料位置。 如需有關資料來源<xref:System.Windows.Forms.DataGridView>控制項支援，請參閱 < [DataGridView 控制項概觀](datagridview-control-overview-windows-forms.md)。  

Visual Studio 的資料繫結至 DataGridView 控制項中的廣泛支援。 如需詳細資訊，請參閱[如何：資料繫結至 Windows Form DataGridView 控制項中使用設計工具](bind-data-to-the-datagrid-using-the-designer.md)。  

若要將 DataGridView 控制項連接至資料：

1. 實作一個方法來處理擷取資料的詳細資料。 下列程式碼範例會實作`GetData`方法，初始化<xref:System.Data.SqlClient.SqlDataAdapter>，並使用它來填入<xref:System.Data.DataTable>。 它接著會繫結<xref:System.Data.DataTable>至<xref:System.Windows.Forms.BindingSource>。 

2. 在表單的<xref:System.Windows.Forms.Form.Load>事件處理常式，繫結<xref:System.Windows.Forms.DataGridView>若要控制<xref:System.Windows.Forms.BindingSource>，並呼叫`GetData`方法來擷取資料。  

## <a name="example"></a>範例

這個完整的程式碼範例會從資料庫填入在 Windows form DataGridView 控制項擷取資料。 此表單還有按鈕來重新載入資料，並將變更提交至資料庫。  

這個範例需要： 

- Northwind SQL Server 範例資料庫的存取。 如需有關如何安裝 Northwind 範例資料庫的詳細資訊，請參閱 <<c0> [ 取得範例資料庫的 ADO.NET 程式碼範例](../../data/adonet/sql/linq/downloading-sample-databases.md)。 

- System、 System.Windows.Forms、 System.Data 和 System.Xml 組件的參考。  

若要建置並執行此範例中，貼上程式碼插入*Form1*中新的 Windows Form 專案的程式碼檔案。 如需從建置C#或 Visual Basic 命令列，請參閱[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)或是[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)。  
  
填入`connectionString`變數中的範例 Northwind SQL Server 範例資料庫連線的值。 Windows 驗證，也稱為整合式的安全性，是更安全的方式，來連接到資料庫將會比將密碼儲存在連接字串。 如需連線安全性的詳細資訊，請參閱[保護連接資訊](../../data/adonet/protecting-connection-information.md)。  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Windows Form DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [保護連接資訊](../../data/adonet/protecting-connection-information.md)
