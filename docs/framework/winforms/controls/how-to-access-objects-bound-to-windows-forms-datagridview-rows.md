---
title: HOW TO：存取繫結至 Windows Forms DataGridView 資料列的物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 423e0ce09b643951e51a5fe94fc9f0423bc4879f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624154"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a>HOW TO：存取繫結至 Windows Forms DataGridView 資料列的物件
有時候顯示儲存在商務物件集合中之資料表的資訊會很有用。 當您繫結 <xref:System.Windows.Forms.DataGridView> 控制項至這類集合，則每個公用屬性會顯示在自己的資料行中​​，除非屬性已標示為不可由 <xref:System.ComponentModel.BrowsableAttribute> 瀏覽。 例如，`Customer` 物件的集合可能有 [名稱] 和 [位址] 等資料行。  
  
 如果這些物件包含其他資訊和您想要存取的程式碼，您可透過資料列物件取得。 在下列程式碼範例中，使用者可以選取多個資料列，然後按一下按鈕將發票傳送至每個對應的客戶。  
  
### <a name="to-access-row-bound-objects"></a>若要存取資料列繫結物件  
  
- 請使用 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a>範例  
 完整的程式碼範例包含簡單的 `Customer` 實作以及繫結 <xref:System.Windows.Forms.DataGridView> 至包含幾個 `Customer` 物件的 <xref:System.Collections.ArrayList>。 <xref:System.Windows.Forms.Button?displayProperty=nameWithType> 的 <xref:System.Windows.Forms.Control.Click> 事件處理常式必須透過資料列存取 `Customer` 物件，因為客戶集合並不能從 <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> 事件處理常式的外部存取。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [在 Windows Forms DataGridView 控制項中顯示資料](displaying-data-in-the-windows-forms-datagridview-control.md)
- [如何：將物件繫結至 Windows Forms DataGridView 控制項](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
