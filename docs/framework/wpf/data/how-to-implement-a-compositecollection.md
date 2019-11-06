---
title: 如何：實作 CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: b3450cdc476b7090251a06b5b2b2718d29e18209
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454034"
---
# <a name="how-to-implement-a-compositecollection"></a>如何：實作 CompositeCollection
## <a name="example"></a>範例  
 下列範例顯示如何使用 <xref:System.Windows.Data.CompositeCollection> 類別，將多個集合和專案顯示為一個清單。 在此範例中，`GreekGods` 是 `GreekGod` 自訂物件的 <xref:System.Collections.ObjectModel.ObservableCollection%601>。 系統會定義資料範本，讓 `GreekGod` 物件和 `GreekHero` 物件分別以金色和青色前景色彩顯示。  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
