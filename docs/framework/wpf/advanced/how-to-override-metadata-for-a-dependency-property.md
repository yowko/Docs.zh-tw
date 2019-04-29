---
title: HOW TO：覆寫相依性屬性的中繼資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
ms.openlocfilehash: 7f20708722660aa4f86462efd50939935f840613
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768624"
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a><span data-ttu-id="cdeb1-102">HOW TO：覆寫相依性屬性的中繼資料</span><span class="sxs-lookup"><span data-stu-id="cdeb1-102">How to: Override Metadata for a Dependency Property</span></span>
<span data-ttu-id="cdeb1-103">此範例示範如何覆寫預設相依性屬性中繼資料來自繼承的類別，藉由呼叫<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>方法，並提供特定類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-103">This example shows how to override default dependency property metadata that comes from an inherited class, by calling the <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> method and providing type-specific metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdeb1-104">範例</span><span class="sxs-lookup"><span data-stu-id="cdeb1-104">Example</span></span>  
 <span data-ttu-id="cdeb1-105">藉由定義其<xref:System.Windows.PropertyMetadata>，類別可以定義相依性屬性的行為，例如其預設值和屬性系統回呼。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-105">By defining its <xref:System.Windows.PropertyMetadata>, a class can define the dependency property's behaviors, such as its default value and property system callbacks.</span></span> <span data-ttu-id="cdeb1-106">許多相依性屬性類別都已經有建立為其註冊程序一部分的預設中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-106">Many dependency property classes already have default metadata established as part of their registration process.</span></span> <span data-ttu-id="cdeb1-107">這包括屬於 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 一部分的相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-107">This includes the dependency properties that are part of the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)].</span></span> <span data-ttu-id="cdeb1-108">透過其類別繼承而繼承相依性屬性的類別可以覆寫原始中繼資料；因此，可透過中繼資料變更之屬性的特性會符合所有子類別特定需求。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-108">A class that inherits the dependency property through its class inheritance can override the original metadata so that the characteristics of the property that can be altered through metadata will match any subclass-specific requirements.</span></span>  
  
 <span data-ttu-id="cdeb1-109">屬性系統使用所放入的屬性之前，必須覆寫相依性屬性上的中繼資料 (這等同於具現化可註冊屬性之物件的特定執行個體的時間)。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-109">Overriding metadata on a dependency property must be done prior to that property being placed in use by the property system (this equates to the time that specific instances of objects that register the property are instantiated).</span></span> <span data-ttu-id="cdeb1-110">若要呼叫<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>必須在本身提供為類型的靜態建構函式中執行`forType`參數<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-110">Calls to <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> must be performed within the static constructors of the type that provides itself as the `forType` parameter of <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>.</span></span> <span data-ttu-id="cdeb1-111">如果您嘗試在擁有者類型的執行個體存在之後變更中繼資料，則這不會引發例外狀況，但會在屬性系統中導致不一致的行為。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-111">If you attempt to change metadata once instances of the owner type exist, this will not raise exceptions, but will result in inconsistent behaviors in the property system.</span></span> <span data-ttu-id="cdeb1-112">此外，一種類型只能覆寫中繼資料一次。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-112">Also, metadata can only be overridden once per type.</span></span> <span data-ttu-id="cdeb1-113">後續覆寫相同類型上中繼資料的嘗試將會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-113">Subsequent attempts to override metadata on the same type will raise an exception.</span></span>  
  
 <span data-ttu-id="cdeb1-114">在下列範例中，自訂類別 `MyAdvancedStateControl` 會將 `MyAdvancedStateControl` 針對 `StateProperty` 所提供的中繼資料覆寫為新的屬性中繼資料。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-114">In the following example, the custom class `MyAdvancedStateControl` overrides the metadata provided for `StateProperty` by `MyAdvancedStateControl` with new property metadata.</span></span> <span data-ttu-id="cdeb1-115">例如，在新建構之 `MyAdvancedStateControl` 執行個體上查詢屬性時，`StateProperty` 的預設值現在會是 `true`。</span><span class="sxs-lookup"><span data-stu-id="cdeb1-115">For instance, the default value of the `StateProperty` is now `true` when the property is queried on a newly constructed `MyAdvancedStateControl` instance.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="cdeb1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdeb1-116">See also</span></span>

- <xref:System.Windows.DependencyProperty>
- [<span data-ttu-id="cdeb1-117">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="cdeb1-117">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="cdeb1-118">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="cdeb1-118">Custom Dependency Properties</span></span>](custom-dependency-properties.md)
- [<span data-ttu-id="cdeb1-119">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="cdeb1-119">How-to Topics</span></span>](properties-how-to-topics.md)
