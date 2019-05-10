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
ms.openlocfilehash: 1f6312f9ac8520b2131e1d2d7a7fb996aee6060e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651586"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>HOW TO：在 Windows Forms DataGridView 控制項中使用資料列範本自訂資料列
<xref:System.Windows.Forms.DataGridView>控制項會使用做為基礎的資料列範本，透過資料繫結中，或當您呼叫時，它將加入此控制項的所有資料列<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>方法，而不指定要使用現有的資料列。  
  
 資料列範本可讓您更有效控制的外觀和行為的資料列<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>屬性提供。 資料列範本後，您可以設定任何<xref:System.Windows.Forms.DataGridViewRow>屬性，包括<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>。  
  
 有一些情況下，您必須在其中使用來達成特定效果的資料列範本。 例如，資料列高度資訊無法儲存在<xref:System.Windows.Forms.DataGridViewCellStyle>，因此您必須使用資料列範本來變更所有資料列所使用的預設高度。 資料列範本也適用於當您建立您自己的類別衍生自<xref:System.Windows.Forms.DataGridViewRow>和您想要您新的資料列加入至控制項時所使用的自訂類型。  
  
> [!NOTE]
>  只有在加入資料列時，才使用資料列範本。 您無法變更現有的資料列，藉由變更資料列範本。  
  
### <a name="to-use-the-row-template"></a>若要使用資料列範本  
  
- 從擷取的物件上設定屬性<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>屬性。  
  
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
