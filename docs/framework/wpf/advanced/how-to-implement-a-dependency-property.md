---
title: "如何：實作相依性屬性"
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
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9bc4dee8f0b2eef76e5769ae7da3a13edf7c3300
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="2fb05-102">如何：實作相依性屬性</span><span class="sxs-lookup"><span data-stu-id="2fb05-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="2fb05-103">這個範例示範如何備份[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]屬性<xref:System.Windows.DependencyProperty> 欄位中，進而定義相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="2fb05-103">This example shows how to back a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="2fb05-104">如果您定義自己的屬性，並想要它們支援 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能的許多層面 (包括樣式、資料繫結、繼承、動畫和預設值)，則應該將它們實作為相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="2fb05-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fb05-105">範例</span><span class="sxs-lookup"><span data-stu-id="2fb05-105">Example</span></span>  
 <span data-ttu-id="2fb05-106">下列範例會先註冊相依性屬性藉由呼叫<xref:System.Windows.DependencyProperty.Register%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2fb05-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="2fb05-107">您用來儲存名稱，而且必須是特性之相依性屬性的識別項欄位名稱<xref:System.Windows.DependencyProperty.Name%2A>您選擇的相依性屬性的一部分<xref:System.Windows.DependencyProperty.Register%2A>呼叫時，常值字串後面附加上`Property`。</span><span class="sxs-lookup"><span data-stu-id="2fb05-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="2fb05-108">比方說，如果您註冊相依性屬性與<xref:System.Windows.DependencyProperty.Name%2A>的`Location`，您定義的相依性屬性的識別項欄位也必須命名為`LocationProperty`。</span><span class="sxs-lookup"><span data-stu-id="2fb05-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="2fb05-109">在此範例中，相依性屬性的名稱和其[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]存取子是`State`; 識別項欄位是`StateProperty`; 屬性的型別是<xref:System.Boolean>; 登錄相依性屬性的型別和`MyStateControl`。</span><span class="sxs-lookup"><span data-stu-id="2fb05-109">In this example, the name of the dependency property and its [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="2fb05-110">如果您無法遵循這個命名模式，則設計工具不一定會正確地報告您的屬性，而且屬性系統樣式應用程式的某些方面可能無法如預期運作。</span><span class="sxs-lookup"><span data-stu-id="2fb05-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="2fb05-111">您也可以指定相依性屬性的預設中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2fb05-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="2fb05-112">此範例會將 `State` 相依性屬性的預設值註冊為 `false`。</span><span class="sxs-lookup"><span data-stu-id="2fb05-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="2fb05-113">如需相依性屬性實作方式和原因的詳細資訊，而不是支援 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] 屬性與私用欄位的詳細資訊，請參閱[相依性屬性概觀](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2fb05-113">For more information about how and why to implement a dependency property, as opposed to just backing a [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property with a private field, see [Dependency Properties Overview](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb05-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2fb05-114">See Also</span></span>  
 [<span data-ttu-id="2fb05-115">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="2fb05-115">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="2fb05-116">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="2fb05-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
