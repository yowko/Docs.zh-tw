---
title: HOW TO：在 Windows Forms DataGridView 控制項中使用資料列範本自訂資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966497"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>HOW TO：在 Windows Forms DataGridView 控制項中使用資料列範本自訂資料列
控制項會使用資料列範本作為其透過資料系結或<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>呼叫方法時, 不需指定要使用的現有資料列來加入控制項之所有資料列的基礎。 <xref:System.Windows.Forms.DataGridView>  
  
 [資料列] 範本可讓您更有效地控制資料列的外觀<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>和行為, 而不是屬性提供的內容。 使用資料列範本, 您可以設定任何<xref:System.Windows.Forms.DataGridViewRow>屬性, 包括<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>。  
  
 在某些情況下, 您必須使用資料列範本來達到特定效果。 例如, 資料列高度資訊不能儲存在中<xref:System.Windows.Forms.DataGridViewCellStyle>, 因此您必須使用資料列範本來變更所有資料列所使用的預設高度。 當您建立自己衍生自<xref:System.Windows.Forms.DataGridViewRow>的類別, 而且想要在新的資料列加入控制項時使用自訂類型時, 資料列範本也很有用。  
  
> [!NOTE]
> 只有在加入資料列時, 才會使用資料列範本。 您無法藉由變更資料列範本來變更現有的資料列。  
  
### <a name="to-use-the-row-template"></a>若要使用資料列範本  
  
- 在從<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>屬性抓取的物件上設定屬性。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
