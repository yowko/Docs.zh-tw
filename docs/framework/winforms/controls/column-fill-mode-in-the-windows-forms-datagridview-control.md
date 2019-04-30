---
title: 在 Windows Form DataGridView 控制項中的資料行填入模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], automatically resizing columns
- DataGridView control [Windows Forms], column fill mode
- data grids [Windows Forms], column fill mode
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
ms.openlocfilehash: a85745d39903719ec1e44ccf70df72d472720b7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956277"
---
# <a name="column-fill-mode-in-the-windows-forms-datagridview-control"></a>在 Windows Form DataGridView 控制項中的資料行填入模式
在資料行填滿模式中，<xref:System.Windows.Forms.DataGridView> 控制項會自動調整其資料行的大小，使資料行填滿可用顯示區域的寬度。 只有在必須將每個資料行的寬度保持等於或大於其 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 屬性值時，這個控制項才會顯示水平捲軸。  
  
 每個資料行的調整行為取決於其 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> 屬性。 如果資料行值為 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> (預設值)，則這個屬性的值會從資料行的 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 屬性或控制項的 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 屬性繼承。  
  
 每個資料行都可以使用不同的調整模式，但是任何使用 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> 調整模式的資料行都會共用其他資料行未使用的顯示區域寬度。 這個寬度會按照所有填滿模式資料行之 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性值的相對比例來分割。 例如，如果兩個資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值為 100 和 200，則第一個資料行寬度會是第二個資料行寬度的一半。  
  
## <a name="user-resizing-in-fill-mode"></a>使用者在填滿模式中調整大小  
 不同於調整模式是根據儲存格內容來調整大小，填滿模式不會防止使用者調整 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> 屬性值為 `true` 的資料行大小。 當使用者調整填滿模式資料行的大小時，已調整大小之資料行後的任何填滿模式資料行 (如果 <xref:System.Windows.Forms.Control.RightToLeft%2A> 為 `false`，則為右側，否則為左側) 也會調整大小，以補償可用寬度的變更。 如果已調整大小的資料行後沒有填滿模式資料行，則會調整控制項中其他所有填滿模式資料行的大小進行補償。 如果控制項中沒有其他任何填滿模式資料行，則會略過調整大小。 如果已調整非填滿模式資料行的大小，則控制項中所有填滿模式資料行會變更大小進行補償。  
  
 調整填滿模式資料行的大小之後，所有已變更資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值都會按比例調整。 例如，如果有四個填滿模式資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值為 100，將第二個資料行的大小調整為其原始寬度的一半會使 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值變成 100、50、125 和 125。 調整非填滿模式資料行的大小不會變更任何 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值，因為只有在需要維持相同比例時，才會調整填滿模式資料行的大小。  
  
## <a name="content-based-fillweight-adjustment"></a>根據內容調整 FillWeight  
 您可以使用 <xref:System.Windows.Forms.DataGridView> 自動化調整大小方法 (例如 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> 方法)，來初始化填滿模式資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值。 這個方法會先計算資料行顯示其內容所需的寬度。 接著，控制項會調整所有填滿模式資料行的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值，使其比例符合計算出來的寬度比例。 最後，控制項會使用新的 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 比例來調整填滿模式資料行的大小，使控制項中的所有資料行填滿可用的水平空間。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 您可以針對許多不同的情況，使用適當的 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>、<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>、<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 和 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> 屬性值來自訂資料行調整行為。  
  
 下列示範程式碼可讓您針對不同資料行的 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>、<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 和 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 屬性，試驗不同的值。 在這個範例中，<xref:System.Windows.Forms.DataGridView> 控制項會繫結至自己的 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合，而且一個資料行會繫結至每一個 <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>、<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>、<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>、<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 和 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> 屬性。 每個資料行也會以控制項中的一個資料列來表示，而變更資料列中的值會更新對應資料行中的屬性，以便您查看這些值的互動方式。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### <a name="comments"></a>註解  
 若要使用這個示範應用程式：  
  
- 變更表單的大小 觀察資料行如何在維持比例 (由 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 屬性值指定) 的同時，變更其寬度。  
  
- 使用滑鼠拖曳資料行分隔線來變更資料行大小。 觀察 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 值如何變更。  
  
- 變更一個資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 值，然後以拖曳方式調整表單的大小。 觀察當表單變得很小時，<xref:System.Windows.Forms.DataGridViewColumn.Width%2A> 值如何維持在 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 值以上。  
  
- 將所有資料行的 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 值變更為較大的數值，讓結合的值超過控制項的寬度。 觀察水平捲軸的顯示方式。  
  
- 變更一些資料行的 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 值。 當您調整資料行或表單的大小時，觀察其效果。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- System、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
- Visual Basic 或 Visual C# 建置此範例從命令列的相關資訊，請參閱[從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或是[命令列使用 csc.exe 建置](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置此範例的 Visual Studio。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=nameWithType>
- [調整 Windows Forms DataGridView 控制項中資料行和資料列的大小](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
