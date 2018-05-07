---
title: 如何：在 Windows Form DataGridView 控制項中使用資料列範本自訂資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 2bde9b3f6934833804866e29c18f3636c65ba069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>如何：在 Windows Form DataGridView 控制項中使用資料列範本自訂資料列
<xref:System.Windows.Forms.DataGridView>控制項使用資料列範本為基礎加入至控制項透過資料繫結，或當您呼叫的所有資料列<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>方法，而不指定要使用現有的資料列。  
  
 資料列範本能讓您進一步控制的外觀和行為的資料列比<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>屬性提供。 資料列範本時，您可以設定任何<xref:System.Windows.Forms.DataGridViewRow>屬性，包括<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>。  
  
 有某些情況下，您必須使用之資料列範本來達到特定的效果。 例如，無法儲存資料列高度的資訊在<xref:System.Windows.Forms.DataGridViewCellStyle>，因此您必須使用資料列範本來變更所有資料列所使用的預設高度。 資料列範本也適用於當您建立您自己的類別衍生自<xref:System.Windows.Forms.DataGridViewRow>，而且您想自訂類型的新資料列加入至控制項時使用。  
  
> [!NOTE]
>  只有在加入資料列時，才使用資料列範本。 變更資料列範本，您無法變更現有的資料列。  
  
### <a name="to-use-the-row-template"></a>若要使用資料列範本  
  
-   從擷取的物件上設定屬性<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>屬性。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=nameWithType>、<xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView 控制項中的基本格式化和樣式設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView 控制項中的儲存格樣式](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
