---
title: HOW TO：將 DataView 物件繫結至 Windows Forms DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: 3a3089073cdc5afb4ee51caca9114b401c740b45
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795011"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a>作法：將 DataView 物件繫結至 Windows Forms DataGridView 控制項
<xref:System.Windows.Forms.DataGridView> 控制項以表格式顯示資料，是一項功能強大、有彈性的方式。 <xref:System.Windows.Forms.DataGridView> 控制項支援標準的 Windows Form 資料繫結模型，因此它將繫結至 <xref:System.Data.DataView> 和各種其他資料來源。 不過，在大部分情況下，您會繫結至 <xref:System.Windows.Forms.BindingSource> 元件，以便管理與資料來源互動的詳細資料。  
  
 如需控制項的<xref:System.Windows.Forms.DataGridView>詳細資訊，請參閱[DataGridView 控制項總覽](../../winforms/controls/datagridview-control-overview-windows-forms.md)。  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a>若要將 DataGridView 控制項連接至 DataView  
  
1. 實作一種方法來處理從資料庫中擷取資料的詳細資料。 下列程式碼範例會實作 `GetData` 方法，而此方法會初始化 <xref:System.Data.SqlClient.SqlDataAdapter> 元件並用它來填入 <xref:System.Data.DataSet>。 請務必將 `connectionString` 變數設定為適用於您資料庫的值。 您將需要已安裝 AdventureWorks SQL Server 範例資料庫之伺服器的存取權。  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. 在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至 <xref:System.Windows.Forms.BindingSource> 元件並呼叫 `GetData` 方法，以便從資料庫中擷取資料。 是從連絡人<xref:System.Data.DataTable>的 LINQ to DataSet 查詢建立，然後再系結至<xref:System.Windows.Forms.BindingSource>元件。 <xref:System.Data.DataView>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a>另請參閱

- [資料繫結和 LINQ to DataSet](data-binding-and-linq-to-dataset.md)
