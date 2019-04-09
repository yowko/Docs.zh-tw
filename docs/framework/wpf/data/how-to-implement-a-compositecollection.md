---
title: HOW TO：實作 CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 8361c2bfa9c125aeadf0a62ca86af1855e5c3dbc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091157"
---
# <a name="how-to-implement-a-compositecollection"></a>HOW TO：實作 CompositeCollection
## <a name="example"></a>範例  
 下列範例示範如何在多個集合和項目顯示為一個清單使用<xref:System.Windows.Data.CompositeCollection>類別。 在此範例中，`GreekGods`已<xref:System.Collections.ObjectModel.ObservableCollection%601>的`GreekGod`自訂物件。 定義資料範本，讓`GreekGod`物件和`GreekHero`物件分別出現與金級和青色的前景色彩。  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [資料繫結概觀](data-binding-overview.md)
- [HOW TO 主題](data-binding-how-to-topics.md)
