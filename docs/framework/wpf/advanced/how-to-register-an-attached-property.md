---
title: 如何：註冊附加屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: e6b0b461552811c5b3fca46a11f087f710e3b2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544072"
---
# <a name="how-to-register-an-attached-property"></a><span data-ttu-id="da378-102">如何：註冊附加屬性</span><span class="sxs-lookup"><span data-stu-id="da378-102">How to: Register an Attached Property</span></span>
<span data-ttu-id="da378-103">此範例示範如何註冊附加屬性，以及提供公用存取子，讓您可以透過 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 和程式碼使用此屬性。</span><span class="sxs-lookup"><span data-stu-id="da378-103">This example shows how to register an attached property and provide public accessors so that you can use the property in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and code.</span></span> <span data-ttu-id="da378-104">附加屬性是透過 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 所定義的語法概念。</span><span class="sxs-lookup"><span data-stu-id="da378-104">Attached properties are a syntax concept defined by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="da378-105">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 類型的大部分附加屬性也會以相依性屬性的方式實作。</span><span class="sxs-lookup"><span data-stu-id="da378-105">Most attached properties for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] types are also implemented as dependency properties.</span></span> <span data-ttu-id="da378-106">您可以使用相依性屬性上任何<xref:System.Windows.DependencyObject>型別。</span><span class="sxs-lookup"><span data-stu-id="da378-106">You can use dependency properties on any <xref:System.Windows.DependencyObject> types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da378-107">範例</span><span class="sxs-lookup"><span data-stu-id="da378-107">Example</span></span>  
 <span data-ttu-id="da378-108">下列範例示範如何使用相依性屬性，以註冊附加的屬性<xref:System.Windows.DependencyProperty.RegisterAttached%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="da378-108">The following example shows how to register an attached property as a dependency property, by using the <xref:System.Windows.DependencyProperty.RegisterAttached%2A> method.</span></span> <span data-ttu-id="da378-109">提供者類別可以選擇提供在另一個類別上使用屬性時所適用屬性的預設中繼資料，除非該類別會覆寫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="da378-109">The provider class has the option of providing default metadata for the property that is applicable when the property is used on another class, unless that class overrides the metadata.</span></span> <span data-ttu-id="da378-110">在此範例中，`IsBubbleSource` 屬性的預設值設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="da378-110">In this example, the default value of the `IsBubbleSource` property is set to `false`.</span></span>  
  
 <span data-ttu-id="da378-111">附加屬性的提供者類別 (即使未註冊為相依性屬性也是一樣) 必須提供遵循命名慣例 `Set`*[AttachedPropertyName]* 和 `Get`*[AttachedPropertyName]* 的靜態 get 和 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="da378-111">The provider class for an attached property (even if it is not registered as a dependency property) must provide static get and set accessors that follow the naming convention `Set`*[AttachedPropertyName]* and `Get`*[AttachedPropertyName]*.</span></span> <span data-ttu-id="da378-112">這些存取子是必要的，因此正在處理的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 讀取器可以將該屬性 (property) 辨識為 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中的屬性 (attribute)，並解析適當的類型。</span><span class="sxs-lookup"><span data-stu-id="da378-112">These accessors are required so that the acting [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader can recognize the property as an attribute in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and resolve the appropriate types.</span></span>  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a><span data-ttu-id="da378-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da378-113">See Also</span></span>  
 <xref:System.Windows.DependencyProperty>  
 [<span data-ttu-id="da378-114">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="da378-114">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [<span data-ttu-id="da378-115">自訂相依性屬性</span><span class="sxs-lookup"><span data-stu-id="da378-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="da378-116">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="da378-116">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
