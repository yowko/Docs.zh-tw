---
title: HOW TO：取得資料集合的預設檢視
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], creating views of
- data binding [WPF], creating views of data collections
ms.assetid: b641e96c-c2f6-42ea-9c5d-bac81176ad65
ms.openlocfilehash: 746331e69ee1e5eee795a0e35202f4889b72c53f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222103"
---
# <a name="how-to-get-the-default-view-of-a-data-collection"></a>HOW TO：取得資料集合的預設檢視
檢視可讓在不同的方式，取決於排序、 篩選或群組準則中檢視相同的資料收集。 每個集合都有一個共用的預設檢視，繫結會指定做為其來源集合時，可做為實際的繫結來源。 此範例示範如何取得集合的預設檢視。  
  
## <a name="example"></a>範例  
 若要建立檢視時，您會需要集合的物件參考。 藉由參考您自己的程式碼後置物件，藉由取得資料內容，取得屬性的資料來源，或取得繫結的屬性，可取得這個資料物件。 此範例示範如何取得<xref:System.Windows.FrameworkElement.DataContext%2A>的資料物件，並使用它來直接取得預設集合檢視此集合。  
  
 [!code-csharp[CollectionView#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#2)]
 [!code-vb[CollectionView#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#2)]  
  
 在此範例中，根項目是<xref:System.Windows.Controls.StackPanel>。 <xref:System.Windows.FrameworkElement.DataContext%2A>設定為*myDataSource*，就是指的資料提供者<xref:System.Collections.ObjectModel.ObservableCollection%601>的*順序*物件。  
  
 [!code-xaml[CollectionView#CollectionViewDataContext](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml#collectionviewdatacontext)]  
  
 或者，您可以具現化，並繫結至您的集合檢視使用<xref:System.Windows.Data.CollectionViewSource>類別。 此集合檢視只會共用直接繫結至它的控制項。 如需範例，請參閱 「 如何建立檢視一節中[資料繫結概觀](data-binding-overview.md)。  
  
 集合檢視所提供之功能的範例，請參閱[檢視中的排序資料](how-to-sort-data-in-a-view.md)，[檢視中的篩選資料](how-to-filter-data-in-a-view.md)，和[瀏覽透過物件在資料 CollectionView](how-to-navigate-through-the-objects-in-a-data-collectionview.md).  
  
## <a name="see-also"></a>另請參閱

- [使用 XAML 中的檢視排序和分組資料](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [HOW TO 主題](data-binding-how-to-topics.md)
