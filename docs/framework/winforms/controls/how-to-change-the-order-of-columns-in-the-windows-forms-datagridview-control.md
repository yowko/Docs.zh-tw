---
title: 如何：變更 Windows Form DataGridView 控制項資料行的順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: f3b1ddd583f76ab135d13108f8c62775ab894c83
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43419174"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>如何：變更 Windows Form DataGridView 控制項資料行的順序
當您使用 <xref:System.Windows.Forms.DataGridView> 顯示來自資料來源的資料時，資料來源結構描述中的資料行有時不會以您想要的順序顯示。 您可以使用 <xref:System.Windows.Forms.DataGridViewColumn> 類別的 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> 屬性來變更資料行的顯示順序。  
  
 下列程式碼範例會重新調整繫結至 Northwind 範例資料庫中的 Customers 資料表時，所自動產生之一些資料行的位置。 如需有關如何將繫結<xref:System.Windows.Forms.DataGridView>控制資料庫資料表，請參閱 <<c2> [ 如何： 將資料繫結至 Windows Form DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 在 Visual Studio 中會支援這項工作。  另請參閱[如何： 變更 Windows Form DataGridView 控制項使用設計工具中的資料行順序](https://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))  
  
## <a name="example"></a>範例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `customersDataGridView` 的 <xref:System.Windows.Forms.DataGridView> 控制項，這個控制項會繫結至具有指定資料行名稱的資料表，例如 Northwind 範例資料庫中的 `Customers` 資料表。  
  
-   <xref:System?displayProperty=nameWithType>、<xref:System.Windows.Forms?displayProperty=nameWithType>、<xref:System.Data?displayProperty=nameWithType> 和 <xref:System.Xml?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [在 Windows Forms DataGridView 控制項中顯示資料](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [操作說明：將資料繫結至 Windows Forms DataGridView 控制項](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
