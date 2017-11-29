---
title: "如何：加入相依性屬性的擁有者類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 079f08e1c330b710748ea6bb1aab8ccfb7ae7016
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="c4abd-102">如何：加入相依性屬性的擁有者類型</span><span class="sxs-lookup"><span data-stu-id="c4abd-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="c4abd-103">這個範例示範如何將類別加入做為註冊不同類型的相依性屬性的擁有者。</span><span class="sxs-lookup"><span data-stu-id="c4abd-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="c4abd-104">這樣做， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]讀取器和屬性系統都能夠辨識類別做為其他擁有者的屬性。</span><span class="sxs-lookup"><span data-stu-id="c4abd-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="c4abd-105">選擇性地加入做為擁有者可讓加入的類別，以提供特定類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c4abd-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="c4abd-106">在下列範例中，`StateProperty`屬性是否註冊`MyStateControl`類別。</span><span class="sxs-lookup"><span data-stu-id="c4abd-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="c4abd-107">類別`UnrelatedStateControl`將本身新增的擁有者為`StateProperty`使用<xref:System.Windows.DependencyProperty.AddOwner%2A>方法，特別使用存在於加入型別，可讓新的相依性屬性中繼資料的簽章。</span><span class="sxs-lookup"><span data-stu-id="c4abd-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="c4abd-108">請注意，您應該提供[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]類似於範例所示的屬性存取子[實作相依性屬性](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)範例中，以及重新公開的類別加入相依性屬性的識別項做為擁有者。</span><span class="sxs-lookup"><span data-stu-id="c4abd-108">Notice that you should provide [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accessors for the property similar to the example shown in the [Implement a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="c4abd-109">沒有包裝函式，相依性屬性將仍可運作以程式設計方式存取使用的觀點<xref:System.Windows.DependencyObject.GetValue%2A>或<xref:System.Windows.DependencyObject.SetValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="c4abd-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="c4abd-110">但您通常想要平行的這個屬性系統行為[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]屬性的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="c4abd-110">But you typically want to parallel this property-system behavior with the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrappers.</span></span> <span data-ttu-id="c4abd-111">包裝函式更輕鬆地以程式設計的方式，設定相依性屬性，並使其可設定為屬性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性。</span><span class="sxs-lookup"><span data-stu-id="c4abd-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="c4abd-112">若要了解如何覆寫預設的中繼資料，請參閱[覆寫相依性屬性的中繼資料](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)。</span><span class="sxs-lookup"><span data-stu-id="c4abd-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4abd-113">範例</span><span class="sxs-lookup"><span data-stu-id="c4abd-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="c4abd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4abd-114">See Also</span></span>  
 [<span data-ttu-id="c4abd-115">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="c4abd-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="c4abd-116">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="c4abd-116">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
