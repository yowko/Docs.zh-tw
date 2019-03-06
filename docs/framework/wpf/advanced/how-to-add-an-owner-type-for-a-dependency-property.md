---
title: HOW TO：加入相依性屬性的擁有者類型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 03ffec87c98c88452aa8fde89c64646eaf48a8da
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369587"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="fc40e-102">HOW TO：加入相依性屬性的擁有者類型</span><span class="sxs-lookup"><span data-stu-id="fc40e-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="fc40e-103">此範例示範如何將類別新增為相依性屬性註冊不同類型的擁有者。</span><span class="sxs-lookup"><span data-stu-id="fc40e-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="fc40e-104">這樣做， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器和屬性系統都能夠辨識為其他屬性的擁有者的類別。</span><span class="sxs-lookup"><span data-stu-id="fc40e-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="fc40e-105">（選擇性） 新增為擁有者，可讓新增的類別，以提供特定類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fc40e-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="fc40e-106">在下列範例中，`StateProperty`屬性的註冊`MyStateControl`類別。</span><span class="sxs-lookup"><span data-stu-id="fc40e-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="fc40e-107">此類別`UnrelatedStateControl`將本身新增為擁有者`StateProperty`使用<xref:System.Windows.DependencyProperty.AddOwner%2A>方法，特別使用存在於將型別，可讓新的相依性屬性中繼資料的簽章。</span><span class="sxs-lookup"><span data-stu-id="fc40e-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="fc40e-108">請注意，您應該提供[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]類似於範例所示的屬性存取子[實作相依性屬性](how-to-implement-a-dependency-property.md)範例中，以及重新公開類別 order_filled 上的相依性屬性識別項身為擁有者。</span><span class="sxs-lookup"><span data-stu-id="fc40e-108">Notice that you should provide [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accessors for the property similar to the example shown in the [Implement a Dependency Property](how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="fc40e-109">包裝函式，沒有相依性屬性仍會正常以程式設計方式存取使用的觀點<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="fc40e-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="fc40e-110">但您通常想要平行處理這類屬性系統行為[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性包裝函式。</span><span class="sxs-lookup"><span data-stu-id="fc40e-110">But you typically want to parallel this property-system behavior with the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrappers.</span></span> <span data-ttu-id="fc40e-111">包裝函式讓您更輕鬆地以程式設計的方式，設定相依性屬性，並使您能夠設定做為屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性。</span><span class="sxs-lookup"><span data-stu-id="fc40e-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="fc40e-112">若要了解如何覆寫預設的中繼資料，請參閱[覆寫相依性屬性的中繼資料](how-to-override-metadata-for-a-dependency-property.md)。</span><span class="sxs-lookup"><span data-stu-id="fc40e-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc40e-113">範例</span><span class="sxs-lookup"><span data-stu-id="fc40e-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="fc40e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc40e-114">See also</span></span>
- [<span data-ttu-id="fc40e-115">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="fc40e-115">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="fc40e-116">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="fc40e-116">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
