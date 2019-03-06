---
title: HOW TO：實作 CompositeCollection
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: 71d55a23711b116a91386a537d5572e8506d4c6b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372668"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="a5476-102">HOW TO：實作 CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="a5476-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="a5476-103">範例</span><span class="sxs-lookup"><span data-stu-id="a5476-103">Example</span></span>  
 <span data-ttu-id="a5476-104">下列範例示範如何在多個集合和項目顯示為一個清單使用<xref:System.Windows.Data.CompositeCollection>類別。</span><span class="sxs-lookup"><span data-stu-id="a5476-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="a5476-105">在此範例中，`GreekGods`已<xref:System.Collections.ObjectModel.ObservableCollection%601>的`GreekGod`自訂物件。</span><span class="sxs-lookup"><span data-stu-id="a5476-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="a5476-106">定義資料範本，讓`GreekGod`物件和`GreekHero`物件分別出現與金級和青色的前景色彩。</span><span class="sxs-lookup"><span data-stu-id="a5476-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a5476-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5476-107">See also</span></span>
- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="a5476-108">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="a5476-108">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="a5476-109">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="a5476-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
