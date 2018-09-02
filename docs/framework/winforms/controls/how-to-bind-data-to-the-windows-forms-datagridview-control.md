---
title: 如何：將資料繫結至 Windows Forms DataGridView 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 4064ef26ee550c02ac8825ac4c1a417472b64de6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419918"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>如何：將資料繫結至 Windows Forms DataGridView 控制項
<xref:System.Windows.Forms.DataGridView> 控制項支援標準的 Windows Form 資料繫結模型，因此會繫結至各種資料來源。 不過，在大部分情況下，您會繫結至 <xref:System.Windows.Forms.BindingSource> 元件，以便管理與資料來源互動的詳細資料。 <xref:System.Windows.Forms.BindingSource> 元件可代表任何 Windows Form 資料來源，並可讓您更彈性地選擇或修改資料的位置。 如需所支援的資料來源<xref:System.Windows.Forms.DataGridView>控制項，請參閱[DataGridView 控制項概觀](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  另請參閱[如何：使用設計工具將資料繫結至 Windows Forms DataGridView 控制項](https://msdn.microsoft.com/library/33w255ac\(v=vs.110\))。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a>將 DataGridView 控制項連接到資料  
  
1.  實作一種方法來處理從資料庫中擷取資料的詳細資料。 下列程式碼範例會實作初始化 <xref:System.Data.SqlClient.SqlDataAdapter> 元件的 `GetData` 方法，並使用它來填入 <xref:System.Data.DataTable>。 <xref:System.Data.DataTable> 會接著繫結至 <xref:System.Windows.Forms.BindingSource> 元件。 請務必將 `connectionString` 變數設定為適用於您資料庫的值。 您將需要已安裝 Northwind SQL Server 範例資料庫之伺服器的存取權。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  在表單的 <xref:System.Windows.Forms.Form.Load> 事件處理常式中，將 <xref:System.Windows.Forms.DataGridView> 控制項繫結至 <xref:System.Windows.Forms.BindingSource> 元件並呼叫 `GetData` 方法，以便從資料庫中擷取資料。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a>範例  
 下列完整的程式碼範例會提供按鈕，以從資料庫重新載入資料，並將變更提交至資料庫。  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Windows.Forms、System.Data 和 System.XML 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在連接字串內儲存機密資訊 (例如密碼) 會影響應用程式的安全性。 使用 Windows 驗證 (也稱為整合式安全性) 是控制資料庫存取的更安全方式。 如需詳細資訊，請參閱[保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [保護連線資訊](../../../../docs/framework/data/adonet/protecting-connection-information.md)
