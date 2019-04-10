---
title: HOW TO：擴充 Windows Forms DataGridView 控制項之儲存格和資料行的行為和外觀，以自訂儲存格和資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 6b0773b4c41b77fe43a5b7fba994778ae18c16c1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325003"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>HOW TO：擴充 Windows Forms DataGridView 控制項之儲存格和資料行的行為和外觀，以自訂儲存格和資料行
<xref:System.Windows.Forms.DataGridView> 控制項提供數種方法使用屬性、事件和附屬類別來自訂其外觀和行為。 有時候除了這些功能可提供的以外，您可能有對於儲存格的更多需求。 您可以建立自己的自訂 <xref:System.Windows.Forms.DataGridViewCell> 類別來提供擴充功能。  
  
 藉由衍生自 <xref:System.Windows.Forms.DataGridViewCell> 基底類別或其中一個衍生的類別，您可建立自訂的 <xref:System.Windows.Forms.DataGridViewCell> 類別。 雖然您可以在任何類型的資料行中顯示任何類型的儲存格，您通常也會建立自訂的 <xref:System.Windows.Forms.DataGridViewColumn> 類別，專門用於顯示儲存格類型。 資料行類別衍生自 <xref:System.Windows.Forms.DataGridViewColumn> 或其衍生類型之一。  
  
 在下列程式碼範例中，您將建立自訂儲存格類別，稱為 `DataGridViewRolloverCell`，偵測滑鼠何時進入及離開儲存格邊界。 當滑鼠在儲存格的邊界內時，會繪製內凹矩形。 這個新的類型衍生自 <xref:System.Windows.Forms.DataGridViewTextBoxCell>，在其他方面的行為如同其基底類別。 附屬資料行類別稱為 `DataGridViewRolloverColumn`。  
  
 若要使用這些類別，請建立一個表單，其中包含 <xref:System.Windows.Forms.DataGridView> 控制項，以及加入一個以上的 `DataGridViewRolloverColumn` 物件到 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合，並在控制項填入包含值的資料列。  
  
> [!NOTE]
>  如果您加入空白資料列，此範例將無法正確運作。 例如當您藉由設定 <xref:System.Windows.Forms.DataGridView.RowCount%2A> 屬性加入資料列至控制項時，會建立空白資料列。 這是因為在此情況下加入的資料列會自動共用，這表示 `DataGridViewRolloverCell` 物件不會具現化，直到您按一下個別的儲存格，因而導致相關的資料列變成非共用的。  
  
 因為自訂這種類型的儲存格需要非共用的資料列，所以它並不適用於大型資料集的使用。 如需有關共用資料列的詳細資訊，請參閱[縮放 Windows Form DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
> [!NOTE]
>  當您自 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 中衍生時，以及在衍生類別中加入新的屬性時，請務必覆寫 `Clone` 方法，在複製作業期間複製新的屬性。 您也應該呼叫基底類別的 `Clone` 方法，以便將基底類別的屬性複製到新的儲存格或資料行。  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>若要自訂 DataGridView 控制項中的資料格和資料行  
  
1. 從 <xref:System.Windows.Forms.DataGridViewTextBoxCell> 類型衍生新的儲存格類別，稱為 `DataGridViewRolloverCell`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2. 覆寫 <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> 類別中的 `DataGridViewRolloverCell` 方法。 在覆寫時，先呼叫基底類別實作，這會處理裝載的文字方塊功能。 然後使用控制項的 <xref:System.Windows.Forms.Control.PointToClient%2A> 方法，將游標位置 (以螢幕座標表示) 轉換為 <xref:System.Windows.Forms.DataGridView> 工作區座標。 如果滑鼠座標落在儲存格的邊界內，則繪製內凹矩形。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3. 覆寫 `DataGridViewRolloverCell` 類別中的 <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> 和 <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> 方法，當滑鼠指標進入或離開儲存格時，強制重新繪製儲存格。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4. 從 <xref:System.Windows.Forms.DataGridViewColumn> 類型衍生新的類別，稱為 `DataGridViewRolloverCellColumn`。 在建構函式中，指派新的 `DataGridViewRolloverCell` 物件至其 <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> 屬性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>範例  
 完整的程式碼範例包含小型測試表單，會示範自訂儲存格類型的行為。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Windows.Forms 和 System.Drawing 組件的參考。  
  
 Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [自訂 Windows Form DataGridView 控制項](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView 控制項架構](datagridview-control-architecture-windows-forms.md)
- [Windows Form DataGridView 控制項中的資料行類型](column-types-in-the-windows-forms-datagridview-control.md)
- [縮放 Windows Form DataGridView 控制項的最佳作法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
