---
title: HOW TO：建立 Grid 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: ebb9369da73bd595338e5b6ef42bda639bde6ed4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134533"
---
# <a name="how-to-create-a-grid-element"></a>HOW TO：建立 Grid 元素
## <a name="example"></a>範例  
 下列範例示範如何建立和使用的執行個體<xref:System.Windows.Controls.Grid>使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或程式碼。 這個範例會使用三個<xref:System.Windows.Controls.ColumnDefinition>物件和三個<xref:System.Windows.Controls.RowDefinition>物件來建立一個方格，其中擁有九個資料格，例如工作表。 每個資料格都包含<xref:System.Windows.Controls.TextBlock>項目，表示資料及上方資料列包含<xref:System.Windows.Controls.TextBlock>使用<xref:System.Windows.Controls.Grid.ColumnSpan%2A>套用的屬性。 若要顯示的界限，每個資料格，<xref:System.Windows.Controls.Grid.ShowGridLines%2A>屬性處於啟用狀態。  
  
 [!code-csharp[Grid#3](~/samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](~/samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  兩種方法會產生看起來相同，類似下面這個使用者介面。

  ![螢幕擷取畫面說明包含分成三個資料行的方格的 WPF 使用者介面。  它具有 '2018年產品出貨' 跨越的頂端列中，所有資料行標題，並有三個資料行每個銷售數字與特定一季。  下方的資料列具有跨越兩個資料行與訊息的文字 ' 總單位：300,000'](././media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.Grid>
- [面板概觀](panels-overview.md)
