---
title: 如何：建立 ListView 的自訂檢視模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: 3b9ca17bddcecb1895205fca76f0a489ecf25c4f
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243215"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>如何:為清單檢視建立自訂檢視模式

此示例演示如何為<xref:System.Windows.Controls.ListView.View%2A><xref:System.Windows.Controls.ListView>控制項創建自定義模式。  
  
## <a name="example"></a>範例  
 在為<xref:System.Windows.Controls.ListView>控制項創建自訂<xref:System.Windows.Controls.ViewBase>檢視時,必須使用該類。 下面的範例顯示從類別的稱為`PlainView`檢視模式<xref:System.Windows.Controls.ViewBase>。  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 要將樣式應用於自訂檢視,請使用類別<xref:System.Windows.Style>。 下面的範例為`PlainView`檢視模式定義<xref:System.Windows.Style>。 在前面的範例中,此樣式設置為為<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>`PlainView`定義的屬性的值。  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 要在自訂檢視模式下定義資料的佈局,請定義物件<xref:System.Windows.DataTemplate>。 下面的範例定義可用於在<xref:System.Windows.DataTemplate>`PlainView`檢視模式下顯示資料的 。  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 下面的範例展示如何<xref:System.Windows.ResourceKey>`PlainView`為使用上一個範例中定義<xref:System.Windows.DataTemplate>的檢視模式定義 。  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 如果將<xref:System.Windows.Controls.ListView>屬性設置為資源鍵<xref:System.Windows.Controls.ListView.View%2A>, 則控件可以使用自定義檢視。 下面的範例展示如何`PlainView`指定為的檢視模式<xref:System.Windows.Controls.ListView>。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 有關完整範例,請參閱[具有多個檢視的清單檢視 (C#)](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp)或[具有多個視圖的清單檢視(可視基本檢視)。](https://github.com/dotnet/docs/tree/master/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [如何主題](listview-how-to-topics.md)
- [ListView 概觀](listview-overview.md)
- [GridView 概觀](gridview-overview.md)
