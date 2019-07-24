---
title: HOW TO：新增相依性屬性的擁有者類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 5ddc85d159b4bf81751428c13c234c5e53be8ad4
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401128"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="94446-102">HOW TO：新增相依性屬性的擁有者類型</span><span class="sxs-lookup"><span data-stu-id="94446-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="94446-103">這個範例示範如何加入類別, 做為針對不同類型註冊之相依性屬性的擁有者。</span><span class="sxs-lookup"><span data-stu-id="94446-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="94446-104">如此一來, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器和屬性系統就能夠將類別辨識為屬性的其他擁有者。</span><span class="sxs-lookup"><span data-stu-id="94446-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="94446-105">新增為擁有者可選擇性地允許加入類別, 以提供特定類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="94446-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="94446-106">在下列範例中, `StateProperty`是`MyStateControl`類別所註冊的屬性。</span><span class="sxs-lookup"><span data-stu-id="94446-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="94446-107">類別`UnrelatedStateControl`會`StateProperty` 使用<xref:System.Windows.DependencyProperty.AddOwner%2A>方法, 將本身新增為的擁有者, 特別是使用簽章, 該簽章可讓相依性屬性的新中繼資料存在於加入型別上。</span><span class="sxs-lookup"><span data-stu-id="94446-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="94446-108">請注意, 您應該提供屬性的通用語言執行平臺 (CLR) 存取子, 類似于實作為相依性[屬性](how-to-implement-a-dependency-property.md)範例中所示的範例, 以及重新公開要新增為擁有者之類別的相依性屬性識別碼。</span><span class="sxs-lookup"><span data-stu-id="94446-108">Notice that you should provide common language runtime (CLR) accessors for the property similar to the example shown in the [Implement a Dependency Property](how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="94446-109">如果沒有包裝函式, 相依性屬性仍然可以從使用<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>的程式設計存取觀點來處理。</span><span class="sxs-lookup"><span data-stu-id="94446-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="94446-110">但您通常會想要將這個屬性系統行為與 CLR 屬性包裝函式進行平行處理。</span><span class="sxs-lookup"><span data-stu-id="94446-110">But you typically want to parallel this property-system behavior with the CLR property wrappers.</span></span> <span data-ttu-id="94446-111">包裝函式可讓您以程式設計方式輕鬆設定相依性屬性, 並可將屬性設定[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]為屬性。</span><span class="sxs-lookup"><span data-stu-id="94446-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="94446-112">若要瞭解如何覆寫預設中繼資料, 請參閱覆寫相依性[屬性的中繼資料](how-to-override-metadata-for-a-dependency-property.md)。</span><span class="sxs-lookup"><span data-stu-id="94446-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94446-113">範例</span><span class="sxs-lookup"><span data-stu-id="94446-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="94446-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94446-114">See also</span></span>

- [<span data-ttu-id="94446-115">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="94446-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="94446-116">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="94446-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
