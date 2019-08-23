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
ms.openlocfilehash: ad72c7a7fb11dfe605db4119dde831b47dd7c5a4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962086"
---
# <a name="how-to-find-a-treeviewitem-in-a-treeview"></a>作法：在 TreeView 中尋找 TreeViewItem
<xref:System.Windows.Controls.TreeView>控制項提供便利的方式來顯示階層式資料。 如果您<xref:System.Windows.Controls.TreeView>的系結至資料來源<xref:System.Windows.Controls.TreeView.SelectedItem%2A> , 屬性會提供便利的方式, 讓您快速地抓取選取的資料物件。 通常最好是使用基礎資料物件, 但有時候您可能需要以程式設計方式操作包含<xref:System.Windows.Controls.TreeViewItem>的資料。 例如, 您可能需要以程式設計方式展開<xref:System.Windows.Controls.TreeViewItem>, 或<xref:System.Windows.Controls.TreeView>在中選取不同的專案。  
  
 若要尋找<xref:System.Windows.Controls.TreeViewItem>包含特定資料物件的, 您必須跨越的<xref:System.Windows.Controls.TreeView>每個層級。 中的專案也<xref:System.Windows.Controls.TreeView>可以虛擬化以改善效能。 如果專案可能已虛擬化, 您也必須<xref:System.Windows.Controls.TreeViewItem>瞭解, 以檢查它是否包含資料物件。  
  
## <a name="example"></a>範例  
  
## <a name="description"></a>描述  
 下列範例會在中<xref:System.Windows.Controls.TreeView>搜尋特定物件, 並傳回包含<xref:System.Windows.Controls.TreeViewItem>的物件。 此範例會確保每<xref:System.Windows.Controls.TreeViewItem>個都具現化, 以便能夠搜尋其子專案。 這個範例也適用于未<xref:System.Windows.Controls.TreeView>使用虛擬化專案的情況。  
  
> [!NOTE]
> 下列範例適用于任何<xref:System.Windows.Controls.TreeView>, 而不論基礎資料模型為何, 並會在找到物件之前搜尋每個。 <xref:System.Windows.Controls.TreeViewItem> 另一個具有較佳效能的技術是在資料模型中搜尋指定的物件、追蹤其在資料階層中的位置, 然後<xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView>在中尋找對應的。 不過, 效能較佳的技術需要資料模型的知識, 而且無法針對任何指定<xref:System.Windows.Controls.TreeView>的進行一般化。  
  
## <a name="code"></a>程式碼  
 [!code-csharp[TreeViewFindTVI#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 先前的程式碼依賴會公開<xref:System.Windows.Controls.VirtualizingStackPanel>名為`BringIntoView`之方法的自訂。 下列程式碼會定義自<xref:System.Windows.Controls.VirtualizingStackPanel>定義。  
  
 [!code-csharp[TreeViewFindTVI#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 下列 XAML 顯示如何建立<xref:System.Windows.Controls.TreeView>使用自訂<xref:System.Windows.Controls.VirtualizingStackPanel>的。  
  
 [!code-xaml[TreeViewFindTVI#3](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## <a name="see-also"></a>另請參閱

- [改善 TreeView 的效能](how-to-improve-the-performance-of-a-treeview.md)
