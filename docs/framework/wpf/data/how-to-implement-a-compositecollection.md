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
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="47770-102">如何：實作 CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="47770-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="47770-103">範例</span><span class="sxs-lookup"><span data-stu-id="47770-103">Example</span></span>  
 <span data-ttu-id="47770-104">下列範例顯示如何使用 <xref:System.Windows.Data.CompositeCollection> 類別，將多個集合和專案顯示為一個清單。</span><span class="sxs-lookup"><span data-stu-id="47770-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="47770-105">在此範例中，`GreekGods` 是 `GreekGod` 自訂物件的 <xref:System.Collections.ObjectModel.ObservableCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="47770-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="47770-106">系統會定義資料範本，讓 `GreekGod` 物件和 `GreekHero` 物件分別以金色和青色前景色彩顯示。</span><span class="sxs-lookup"><span data-stu-id="47770-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="47770-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="47770-107">See also</span></span>

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="47770-108">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="47770-108">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="47770-109">「如何」主題</span><span class="sxs-lookup"><span data-stu-id="47770-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
