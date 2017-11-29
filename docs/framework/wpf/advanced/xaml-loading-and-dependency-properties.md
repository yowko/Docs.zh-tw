---
title: "XAML 載入和相依性屬性"
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
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 97970a8a292eee43b01b1eab235376ae9b8e6fad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-loading-and-dependency-properties"></a><span data-ttu-id="1fa41-102">XAML 載入和相依性屬性</span><span class="sxs-lookup"><span data-stu-id="1fa41-102">XAML Loading and Dependency Properties</span></span>
<span data-ttu-id="1fa41-103">目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作，在本質上就會感知相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="1fa41-103">The current [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementation of its [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor is inherently dependency property aware.</span></span> <span data-ttu-id="1fa41-104">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器在載入二進位 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和處理相依性屬性的屬性時，會使用相依性屬性的屬性系統方法。</span><span class="sxs-lookup"><span data-stu-id="1fa41-104">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor uses property system methods for dependency properties when loading binary [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and processing attributes that are dependency properties.</span></span> <span data-ttu-id="1fa41-105">這可有效略過屬性的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="1fa41-105">This effectively bypasses the property wrappers.</span></span> <span data-ttu-id="1fa41-106">當您實作自訂的相依性屬性時，您必須負責這種行為，並置於您的內容包裝函式屬性系統方法以外的任何其他程式碼應該避免<xref:System.Windows.DependencyObject.GetValue%2A>和<xref:System.Windows.DependencyObject.SetValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="1fa41-106">When you implement custom dependency properties, you must account for this behavior and should avoid placing any other code in your property wrapper other than the property system methods <xref:System.Windows.DependencyObject.GetValue%2A> and <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span>  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a><span data-ttu-id="1fa41-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="1fa41-107">Prerequisites</span></span>  
 <span data-ttu-id="1fa41-108">本主題假設您已從相依性屬性的消費者和作者角度了解相依性屬性，並已閱讀[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)和[自訂相依性屬性](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="1fa41-108">This topic assumes that you understand dependency properties both as consumer and author and have read [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) and [Custom Dependency Properties](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).</span></span> <span data-ttu-id="1fa41-109">此外，您應已閱讀 [XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) 和 [XAML 語法詳細資料](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="1fa41-109">You should also have read [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) and [XAML Syntax In Detail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a><span data-ttu-id="1fa41-110">WPF XAML 載入器實作與效能</span><span class="sxs-lookup"><span data-stu-id="1fa41-110">The WPF XAML Loader Implementation, and Performance</span></span>  
 <span data-ttu-id="1fa41-111">基於實作原因，是較不費時屬性做為相依性屬性的識別及存取屬性系統<xref:System.Windows.DependencyObject.SetValue%2A>方法來設定它，而不是使用屬性的包裝函式和其 setter。</span><span class="sxs-lookup"><span data-stu-id="1fa41-111">For implementation reasons, it is computationally less expensive to identify a property as a dependency property and access the property system <xref:System.Windows.DependencyObject.SetValue%2A> method to set it, rather than using the property wrapper and its setter.</span></span> <span data-ttu-id="1fa41-112">這是因為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器僅能藉由各種字串和標記之結構所表示的型別和成員關聯性，來推斷支援程式碼的整個物件模型。</span><span class="sxs-lookup"><span data-stu-id="1fa41-112">This is because a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor must infer the entire object model of the backing code based only on knowing the type and member relationships that are indicated by the structure of the markup and various strings.</span></span>  
  
 <span data-ttu-id="1fa41-113">型別查閱透過 xmlns 和組件屬性，但是識別的成員，決定無法設定屬性，為支援的組合和解決何種類型的屬性值支援否則會需要大量的反映使用<xref:System.Reflection.PropertyInfo>。</span><span class="sxs-lookup"><span data-stu-id="1fa41-113">The type is looked up through a combination of xmlns and assembly attributes, but identifying the members, determining which could support being set as an attribute, and resolving what types the property values support would otherwise require extensive reflection using <xref:System.Reflection.PropertyInfo>.</span></span> <span data-ttu-id="1fa41-114">因為相依性屬性上指定的型別為屬性系統，透過儲存體資料表存取[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]實作其[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理器會使用此資料表，並且推斷的任何給定屬性*ABC*您可以更有效率地將藉由呼叫<xref:System.Windows.DependencyObject.SetValue%2A>上包含<xref:System.Windows.DependencyObject>衍生型別，使用相依性屬性的識別項*ABCProperty*。</span><span class="sxs-lookup"><span data-stu-id="1fa41-114">Because dependency properties on a given type are accessible as a storage table through the property system, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementation of its [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor uses this table and infers that any given property *ABC* can be more efficiently set by calling <xref:System.Windows.DependencyObject.SetValue%2A> on the containing <xref:System.Windows.DependencyObject> derived type, using the dependency property identifier *ABCProperty*.</span></span>  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a><span data-ttu-id="1fa41-115">自訂相依性屬性的影響</span><span class="sxs-lookup"><span data-stu-id="1fa41-115">Implications for Custom Dependency Properties</span></span>  
 <span data-ttu-id="1fa41-116">由於目前 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 處理器的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 實作其屬性設定行為完全略過包裝函式，因此您不應該將任何其他邏輯放入自訂相依性屬性之包裝函式的集合定義中。</span><span class="sxs-lookup"><span data-stu-id="1fa41-116">Because the current [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementation of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor behavior for property setting bypasses the wrappers entirely, you should not put any additional logic into the set definitions of the wrapper for your custom dependency property.</span></span> <span data-ttu-id="1fa41-117">如果您在集合定義中放置這類邏輯，則在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中設定屬性 (而不是在程式碼中設定) 時，將不會執行邏輯。</span><span class="sxs-lookup"><span data-stu-id="1fa41-117">If you put such logic in the set definition, then the logic will not be executed when the property is set in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rather than in code.</span></span>  
  
 <span data-ttu-id="1fa41-118">同樣地，其他方面的[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]取得屬性值的處理器[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]處理也使用<xref:System.Windows.DependencyObject.GetValue%2A>而不是使用包裝函式。</span><span class="sxs-lookup"><span data-stu-id="1fa41-118">Similarly, other aspects of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor that obtain property values from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processing also use <xref:System.Windows.DependencyObject.GetValue%2A> rather than using the wrapper.</span></span> <span data-ttu-id="1fa41-119">因此，您也應該避免在任何其他實作`get`超出定義<xref:System.Windows.DependencyObject.GetValue%2A>呼叫。</span><span class="sxs-lookup"><span data-stu-id="1fa41-119">Therefore, you should also avoid any additional implementation in the `get` definition beyond the <xref:System.Windows.DependencyObject.GetValue%2A> call.</span></span>  
  
 <span data-ttu-id="1fa41-120">下列範例是建議的相依性屬性定義與包裝函式，其中將屬性識別項儲存為 `public` `static` `readonly` 欄位，而 `get` 和 `set` 定義所包含的程式碼也都在定義支援相依性屬性的必要屬性系統方法範圍內。</span><span class="sxs-lookup"><span data-stu-id="1fa41-120">The following example is a recommended dependency property definition with wrappers, where the property identifier is stored as a `public` `static` `readonly` field, and the `get` and `set` definitions contain no code beyond the necessary property system methods that define the dependency property backing.</span></span>  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a><span data-ttu-id="1fa41-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fa41-121">See Also</span></span>  
 [<span data-ttu-id="1fa41-122">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="1fa41-122">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="1fa41-123">XAML 概觀 (WPF)</span><span class="sxs-lookup"><span data-stu-id="1fa41-123">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="1fa41-124">相依性屬性中繼資料</span><span class="sxs-lookup"><span data-stu-id="1fa41-124">Dependency Property Metadata</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [<span data-ttu-id="1fa41-125">集合類型的相依性屬性</span><span class="sxs-lookup"><span data-stu-id="1fa41-125">Collection-Type Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [<span data-ttu-id="1fa41-126">相依性屬性的安全性</span><span class="sxs-lookup"><span data-stu-id="1fa41-126">Dependency Property Security</span></span>](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [<span data-ttu-id="1fa41-127">DependencyObject 的安全建構函式模式</span><span class="sxs-lookup"><span data-stu-id="1fa41-127">Safe Constructor Patterns for DependencyObjects</span></span>](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
