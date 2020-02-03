---
title: 使用資料列範本自訂 DataGridView 控制項中的資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 35cb95f22c0caa654bf149b5fc4fd0395696a411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728392"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>如何：在 Windows Form DataGridView 控制項中使用資料列範本自訂資料列
<xref:System.Windows.Forms.DataGridView> 控制項會使用資料列範本做為其透過資料系結或呼叫 <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> 方法時，不需要指定要使用的現有資料列來加入控制項之所有資料列的基礎。  
  
 [資料列] 範本可讓您更充分掌控資料列的外觀和行為，而不是 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 屬性所提供的。 使用資料列範本，您可以設定任何 <xref:System.Windows.Forms.DataGridViewRow> 的屬性，包括 <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>。  
  
 在某些情況下，您必須使用資料列範本來達到特定效果。 例如，資料列高度資訊不能儲存在 <xref:System.Windows.Forms.DataGridViewCellStyle>中，因此您必須使用資料列範本來變更所有資料列所使用的預設高度。 當您建立衍生自 <xref:System.Windows.Forms.DataGridViewRow> 的自訂類別，而且想要將新的資料列加入至控制項時，就會使用資料列範本，這也很有用。  
  
> [!NOTE]
> 只有在加入資料列時，才會使用資料列範本。 您無法藉由變更資料列範本來變更現有的資料列。  
  
### <a name="to-use-the-row-template"></a>若要使用資料列範本  
  
- 在從 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> 屬性抓取的物件上設定屬性。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
- 名為 <xref:System.Windows.Forms.DataGridView> 的 `dataGridView1` 控制項。  
  
- <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView 控制項中的儲存格樣式](cell-styles-in-the-windows-forms-datagridview-control.md)
