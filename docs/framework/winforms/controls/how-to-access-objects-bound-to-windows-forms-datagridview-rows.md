---
title: 存取繫結至 DataGridView 資料列的物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743173"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>如何：存取物件繫結至 Windows Form DataGridView 資料列
有時候顯示儲存在商務物件集合中之資料表的資訊會很有用。 當您繫結 <xref:System.Windows.Forms.DataGridView> 控制項至這類集合，則每個公用屬性會顯示在自己的資料行中​​，除非屬性已標示為不可由 <xref:System.ComponentModel.BrowsableAttribute> 瀏覽。 例如，`Customer` 物件的集合可能有 [名稱] 和 [位址] 等資料行。  
  
 如果這些物件包含其他資訊和您想要存取的程式碼，您可透過資料列物件取得。 在下列程式碼範例中，使用者可以選取多個資料列，然後按一下按鈕將發票傳送至每個對應的客戶。  
  
### <a name="to-access-row-bound-objects"></a>若要存取資料列繫結物件  
  
- 請使用 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>範例  
 完整的程式碼範例包含簡單的 `Customer` 實作以及繫結 <xref:System.Windows.Forms.DataGridView> 至包含幾個 <xref:System.Collections.ArrayList> 物件的 `Customer`。 <xref:System.Windows.Forms.Control.Click> 的 <xref:System.Windows.Forms.Button?displayProperty=nameWithType> 事件處理常式必須透過資料列存取 `Customer` 物件，因為客戶集合並不能從 <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> 事件處理常式的外部存取。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System 和 System.Windows.Forms 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [如何：將物件繫結至 Windows Forms DataGridView 控制項](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
