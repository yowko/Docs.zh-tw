---
title: HOW TO：實作相依性屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 6f2fb9b0824feb6253527de063f58da2427d0c06
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400364"
---
# <a name="how-to-implement-a-dependency-property"></a><span data-ttu-id="9bf03-102">作法：實作相依性屬性</span><span class="sxs-lookup"><span data-stu-id="9bf03-102">How to: Implement a Dependency Property</span></span>
<span data-ttu-id="9bf03-103">這個範例示範如何使用<xref:System.Windows.DependencyProperty>欄位來回溯 common language runtime (CLR) 屬性, 藉此定義相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf03-103">This example shows how to back a common language runtime (CLR) property with a <xref:System.Windows.DependencyProperty> field, thus defining a dependency property.</span></span> <span data-ttu-id="9bf03-104">如果您定義自己的屬性，並想要它們支援 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 功能的許多層面 (包括樣式、資料繫結、繼承、動畫和預設值)，則應該將它們實作為相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf03-104">When you define your own properties and want them to support many aspects of [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] functionality, including styles, data binding, inheritance, animation, and default values, you should implement them as a dependency property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bf03-105">範例</span><span class="sxs-lookup"><span data-stu-id="9bf03-105">Example</span></span>  
 <span data-ttu-id="9bf03-106">下列範例會先呼叫<xref:System.Windows.DependencyProperty.Register%2A>方法, 以註冊相依性屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf03-106">The following example first registers a dependency property by calling the <xref:System.Windows.DependencyProperty.Register%2A> method.</span></span> <span data-ttu-id="9bf03-107">您用來儲存相依性屬性名稱和特性的識別碼欄位名稱, 必須是<xref:System.Windows.DependencyProperty.Name%2A>您在<xref:System.Windows.DependencyProperty.Register%2A>呼叫過程中為相依性屬性選擇的, 並以常值字串`Property`附加。</span><span class="sxs-lookup"><span data-stu-id="9bf03-107">The name of the identifier field that you use to store the name and characteristics of the dependency property must be the <xref:System.Windows.DependencyProperty.Name%2A> you chose for the dependency property as part of the <xref:System.Windows.DependencyProperty.Register%2A> call, appended by the literal string `Property`.</span></span> <span data-ttu-id="9bf03-108">例如, 如果您使用<xref:System.Windows.DependencyProperty.Name%2A>的來`Location`註冊相依性屬性, 則您為相依性屬性定義的識別碼欄位必須命名為`LocationProperty`。</span><span class="sxs-lookup"><span data-stu-id="9bf03-108">For instance, if you register a dependency property with a <xref:System.Windows.DependencyProperty.Name%2A> of `Location`, then the identifier field that you define for the dependency property must be named `LocationProperty`.</span></span>  
  
 <span data-ttu-id="9bf03-109">在此範例中, 相依性屬性及其 CLR 存取子的名稱是`State`; 識別碼欄位是`StateProperty`; 屬性的類型是<xref:System.Boolean>; 而註冊相依性屬性的類型是`MyStateControl`。</span><span class="sxs-lookup"><span data-stu-id="9bf03-109">In this example, the name of the dependency property and its CLR accessor is `State`; the identifier field is `StateProperty`; the type of the property is <xref:System.Boolean>; and the type that registers the dependency property is `MyStateControl`.</span></span>  
  
 <span data-ttu-id="9bf03-110">如果您無法遵循這個命名模式，則設計工具不一定會正確地報告您的屬性，而且屬性系統樣式應用程式的某些方面可能無法如預期運作。</span><span class="sxs-lookup"><span data-stu-id="9bf03-110">If you fail to follow this naming pattern, designers might not report your property correctly, and certain aspects of property system style application might not behave as expected.</span></span>  
  
 <span data-ttu-id="9bf03-111">您也可以指定相依性屬性的預設中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9bf03-111">You can also specify default metadata for a dependency property.</span></span> <span data-ttu-id="9bf03-112">此範例會將 `State` 相依性屬性的預設值註冊為 `false`。</span><span class="sxs-lookup"><span data-stu-id="9bf03-112">This example registers the default value of the `State` dependency property to be `false`.</span></span>  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 <span data-ttu-id="9bf03-113">如需如何和為何要執行相依性屬性的詳細資訊, 而不只是以私用欄位來支援 CLR 屬性, 請參閱相依性[屬性總覽](dependency-properties-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf03-113">For more information about how and why to implement a dependency property, as opposed to just backing a CLR property with a private field, see [Dependency Properties Overview](dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf03-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bf03-114">See also</span></span>

- [<span data-ttu-id="9bf03-115">相依性屬性概觀</span><span class="sxs-lookup"><span data-stu-id="9bf03-115">Dependency Properties Overview</span></span>](dependency-properties-overview.md)
- [<span data-ttu-id="9bf03-116">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="9bf03-116">How-to Topics</span></span>](properties-how-to-topics.md)
