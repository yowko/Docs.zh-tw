---
title: HOW TO：隱藏 Windows Form DataGridView 控制項中的資料行標頭
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: 80377aa598938031f9708c4b7657594985ec0746
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717060"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a>HOW TO：隱藏 Windows Form DataGridView 控制項中的資料行標頭
有時候您會想要顯示<xref:System.Windows.Forms.DataGridView>不含資料行的標頭。 在 <xref:System.Windows.Forms.DataGridView>控制項，<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>屬性值會決定是否要顯示資料行標頭。  
  
### <a name="to-hide-the-column-headers"></a>若要隱藏資料行行首  
  
-   將 <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> 屬性設定為 `false`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   名為 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控制項。  
  
-   <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 組件的參考。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [Windows Forms DataGridView 控制項中的基本資料行、資料列和儲存格功能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
