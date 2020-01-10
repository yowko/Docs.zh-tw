---
title: 命名空間的名稱
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709227"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="356ef-102">命名空間的名稱</span><span class="sxs-lookup"><span data-stu-id="356ef-102">Names of Namespaces</span></span>
<span data-ttu-id="356ef-103">就像其他命名指導方針一樣，命名命名空間的目標是要讓程式設計人員能夠使用架構來立即知道命名空間的內容有何可能。</span><span class="sxs-lookup"><span data-stu-id="356ef-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="356ef-104">下列範本會指定命名空間的一般規則：</span><span class="sxs-lookup"><span data-stu-id="356ef-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="356ef-105">範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="356ef-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="356ef-106">**✓**會在命名空間名稱前面加上公司名稱，以防止來自不同公司的命名空間具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="356ef-107">**✓**會在命名空間名稱的第二個層級上使用穩定、版本無關的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="356ef-108">**X**不會使用組織階層做為命名空間階層中的名稱基礎，因為公司內的組名通常會短期。</span><span class="sxs-lookup"><span data-stu-id="356ef-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="356ef-109">依據相關技術群組來組織命名空間的階層。</span><span class="sxs-lookup"><span data-stu-id="356ef-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="356ef-110">**✓**會使用 PascalCasing，並以句點（例如 `Microsoft.Office.PowerPoint`）來分隔命名空間元件。</span><span class="sxs-lookup"><span data-stu-id="356ef-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="356ef-111">如果您的品牌採用生命的大小寫，則應該遵循您的品牌所定義的大小寫，即使它與一般的命名空間大小寫不一樣。</span><span class="sxs-lookup"><span data-stu-id="356ef-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="356ef-112">**✓請考慮**在適當時使用複數命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="356ef-113">例如，使用 `System.Collections` 而不是 `System.Collection`。</span><span class="sxs-lookup"><span data-stu-id="356ef-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="356ef-114">不過，品牌名稱和縮寫是此規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="356ef-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="356ef-115">例如，使用 `System.IO` 而不是 `System.IOs`。</span><span class="sxs-lookup"><span data-stu-id="356ef-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="356ef-116">**X**在命名空間和該命名空間中的類型不使用相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="356ef-117">例如，請勿使用 `Debug` 做為命名空間名稱，然後在相同的命名空間中提供名為 `Debug` 的類別。</span><span class="sxs-lookup"><span data-stu-id="356ef-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="356ef-118">數個編譯器要求這類類型必須是完整的。</span><span class="sxs-lookup"><span data-stu-id="356ef-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="356ef-119">命名空間和類型名稱衝突</span><span class="sxs-lookup"><span data-stu-id="356ef-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="356ef-120">**X 不會**引進泛型型別名稱，例如 `Element`、`Node`、`Log`和 `Message`。</span><span class="sxs-lookup"><span data-stu-id="356ef-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="356ef-121">這麼做的機率很高，會導致常見案例中的型別名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="356ef-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="356ef-122">您應該限定泛型型別名稱（`FormElement`、`XmlNode`、`EventLog`、`SoapMessage`）。</span><span class="sxs-lookup"><span data-stu-id="356ef-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="356ef-123">有一些特定的指導方針可避免不同分類命名空間的類型名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="356ef-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
- <span data-ttu-id="356ef-124">**應用程式模型命名空間**</span><span class="sxs-lookup"><span data-stu-id="356ef-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="356ef-125">屬於單一應用程式模型的命名空間通常會一起使用，但它們幾乎不會與其他應用程式模型的命名空間搭配使用。</span><span class="sxs-lookup"><span data-stu-id="356ef-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="356ef-126">例如，<xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間很少與 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間搭配使用。</span><span class="sxs-lookup"><span data-stu-id="356ef-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="356ef-127">以下是知名的應用程式模型命名空間群組清單：</span><span class="sxs-lookup"><span data-stu-id="356ef-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="356ef-128">**X 不會**在單一應用程式模型中，為命名空間中的類型提供相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="356ef-129">例如，請勿將名為 `Page` 的類型加入 <xref:System.Web.UI.Adapters?displayProperty=nameWithType> 命名空間，因為 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間已經包含名為 `Page`的類型。</span><span class="sxs-lookup"><span data-stu-id="356ef-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
- <span data-ttu-id="356ef-130">**基礎結構命名空間**</span><span class="sxs-lookup"><span data-stu-id="356ef-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="356ef-131">此群組包含在開發一般應用程式期間很少匯入的命名空間。</span><span class="sxs-lookup"><span data-stu-id="356ef-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="356ef-132">例如，在開發程式設計工具時，主要會使用 `.Design` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="356ef-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="356ef-133">避免與這些命名空間中的類型發生衝突並不重要。</span><span class="sxs-lookup"><span data-stu-id="356ef-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
- <span data-ttu-id="356ef-134">**核心命名空間**</span><span class="sxs-lookup"><span data-stu-id="356ef-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="356ef-135">核心命名空間包含所有 `System` 的命名空間，但不包括應用程式模型的命名空間和基礎結構命名空間。</span><span class="sxs-lookup"><span data-stu-id="356ef-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="356ef-136">核心命名空間包括其他 `System`、`System.IO`、`System.Xml`和 `System.Net`。</span><span class="sxs-lookup"><span data-stu-id="356ef-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="356ef-137">**X**不會提供與核心命名空間中任何類型衝突的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="356ef-138">例如，絕對不要使用 `Stream` 做為類型名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="356ef-139">它會與 <xref:System.IO.Stream?displayProperty=nameWithType>（非常常用的類型）相衝突。</span><span class="sxs-lookup"><span data-stu-id="356ef-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
- <span data-ttu-id="356ef-140">**技術命名空間群組**</span><span class="sxs-lookup"><span data-stu-id="356ef-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="356ef-141">此類別包含前兩個命名空間節點 `(<Company>.<Technology>*`）的所有命名空間，例如 `Microsoft.Build.Utilities` 和 `Microsoft.Build.Tasks`。</span><span class="sxs-lookup"><span data-stu-id="356ef-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="356ef-142">屬於單一技術的型別不會互相衝突，這點很重要。</span><span class="sxs-lookup"><span data-stu-id="356ef-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="356ef-143">**X**不會指派與單一技術內其他類型衝突的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="356ef-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="356ef-144">**X**不會在技術命名空間中的類型與應用程式模型命名空間之間引進類型名稱衝突（除非此技術不適合用于應用程式模型）。</span><span class="sxs-lookup"><span data-stu-id="356ef-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="356ef-145">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="356ef-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="356ef-146">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="356ef-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356ef-147">請參閱</span><span class="sxs-lookup"><span data-stu-id="356ef-147">See also</span></span>

- [<span data-ttu-id="356ef-148">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="356ef-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="356ef-149">命名方針</span><span class="sxs-lookup"><span data-stu-id="356ef-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
