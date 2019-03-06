---
title: HOW TO：在 TreeView 中尋找 TreeViewItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], finding a TreeViewItem
- TreeViewItem [WPF], finding
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
ms.openlocfilehash: c90db5312d58cfba18910f299386e2884fb36ce6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360213"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>HOW TO：在 TreeView 中尋找 TreeViewItem
<xref:System.Windows.Controls.TreeView>控制項提供便利的方式，來顯示階層式資料。 如果您<xref:System.Windows.Controls.TreeView>繫結至資料來源，<xref:System.Windows.Controls.TreeView.SelectedItem%2A>屬性提供便利的方式，讓您快速擷取選取的資料物件。 通常最好使用基礎資料物件中，但有時候您可能需要以程式設計方式操作的資料包含<xref:System.Windows.Controls.TreeViewItem>。 例如，您可能需要以程式設計方式展開<xref:System.Windows.Controls.TreeViewItem>，或選取不同的項目中<xref:System.Windows.Controls.TreeView>。  
  
 若要尋找<xref:System.Windows.Controls.TreeViewItem>，其中包含特定的資料物件，則必須周遊的每個層級<xref:System.Windows.Controls.TreeView>。 中的項目<xref:System.Windows.Controls.TreeView>也都可以虛擬化來改善效能。 在案例中可能會虛擬化項目，您也必須了解<xref:System.Windows.Controls.TreeViewItem>來檢查它是否包含資料的物件。  
  
## <a name="example"></a>範例  
  
## <a name="description"></a>描述  
 下列範例會搜尋<xref:System.Windows.Controls.TreeView>針對特定物件，並傳回包含之物件的<xref:System.Windows.Controls.TreeViewItem>。 此範例可確保每個<xref:System.Windows.Controls.TreeViewItem>會具現化，而可以搜尋其子項目。 此範例也適用於如果<xref:System.Windows.Controls.TreeView>不會使用虛擬化的項目。  
  
> [!NOTE]
>  下列範例適用於任何<xref:System.Windows.Controls.TreeView>不論基礎資料模型，並搜尋每個<xref:System.Windows.Controls.TreeViewItem>直到找到的物件。 具有較佳的效能的另一個方法是搜尋指定的物件的資料模型、 追蹤內資料階層中，其位置，並找出對應<xref:System.Windows.Controls.TreeViewItem>在<xref:System.Windows.Controls.TreeView>。 不過，有較佳的效能的技巧需要資料模型的知識，而且無法在任何給定的一般化<xref:System.Windows.Controls.TreeView>。  
  
## <a name="code"></a>程式碼  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 先前的程式碼依賴自訂<xref:System.Windows.Controls.VirtualizingStackPanel>公開一個名為方法`BringIntoView`。 下列程式碼會定義自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 下列 XAML 示範如何建立<xref:System.Windows.Controls.TreeView>使用自訂<xref:System.Windows.Controls.VirtualizingStackPanel>。  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>另請參閱
- [改善 TreeView 的效能](how-to-improve-the-performance-of-a-treeview.md)
