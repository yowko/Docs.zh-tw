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
author: KrzysztofCwalina
ms.openlocfilehash: 64efdc46583a0931df9f57c32424ca4233bf2b82
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143437"
---
# <a name="names-of-namespaces"></a><span data-ttu-id="d0eee-102">命名空間的名稱</span><span class="sxs-lookup"><span data-stu-id="d0eee-102">Names of Namespaces</span></span>
<span data-ttu-id="d0eee-103">做為其他命名指導方針，命名的命名空間時的目標建立足夠的清晰度給程式設計人員立即知道命名空間的內容可能是使用架構。</span><span class="sxs-lookup"><span data-stu-id="d0eee-103">As with other naming guidelines, the goal when naming namespaces is creating sufficient clarity for the programmer using the framework to immediately know what the content of the namespace is likely to be.</span></span> <span data-ttu-id="d0eee-104">下列範本指定為命名空間進行的一般規則：</span><span class="sxs-lookup"><span data-stu-id="d0eee-104">The following template specifies the general rule for naming namespaces:</span></span>  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 <span data-ttu-id="d0eee-105">以下是範例：</span><span class="sxs-lookup"><span data-stu-id="d0eee-105">The following are examples:</span></span>  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 <span data-ttu-id="d0eee-106">**✓ DO** 命名空間名稱前面加上的公司名稱，以避免不同公司的具有相同名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d0eee-106">**✓ DO** prefix namespace names with a company name to prevent namespaces from different companies from having the same name.</span></span>  
  
 <span data-ttu-id="d0eee-107">**✓ DO** 第二個層級的命名空間名稱使用的穩定、 版本無關的產品名稱。</span><span class="sxs-lookup"><span data-stu-id="d0eee-107">**✓ DO** use a stable, version-independent product name at the second level of a namespace name.</span></span>  
  
 <span data-ttu-id="d0eee-108">**X DO NOT** 使用組織階層做為基礎，名稱在命名空間階層中，因為公司內的群組名稱大多數為暫時性。</span><span class="sxs-lookup"><span data-stu-id="d0eee-108">**X DO NOT** use organizational hierarchies as the basis for names in namespace hierarchies, because group names within corporations tend to be short-lived.</span></span> <span data-ttu-id="d0eee-109">組織相關技術的群組周圍的命名空間階層的架構。</span><span class="sxs-lookup"><span data-stu-id="d0eee-109">Organize the hierarchy of namespaces around groups of related technologies.</span></span>  
  
 <span data-ttu-id="d0eee-110">**✓ DO** 期間，使用 PascalCasing，與不同的命名空間的元件 (例如 `Microsoft.Office.PowerPoint`)。</span><span class="sxs-lookup"><span data-stu-id="d0eee-110">**✓ DO** use PascalCasing, and separate namespace components with periods (e.g., `Microsoft.Office.PowerPoint`).</span></span> <span data-ttu-id="d0eee-111">如果您的品牌採用非傳統任務為大小寫，則您應該遵循您的品牌所定義的大小寫，即使它是衍生自標準的命名空間的大小寫。</span><span class="sxs-lookup"><span data-stu-id="d0eee-111">If your brand employs nontraditional casing, you should follow the casing defined by your brand, even if it deviates from normal namespace casing.</span></span>  
  
 <span data-ttu-id="d0eee-112">**✓ CONSIDER** 適時使用複數命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="d0eee-112">**✓ CONSIDER** using plural namespace names where appropriate.</span></span>  
  
 <span data-ttu-id="d0eee-113">例如，使用`System.Collections`而不是`System.Collection`。</span><span class="sxs-lookup"><span data-stu-id="d0eee-113">For example, use `System.Collections` instead of `System.Collection`.</span></span> <span data-ttu-id="d0eee-114">品牌名稱與縮寫不過是這項規則的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d0eee-114">Brand names and acronyms are exceptions to this rule, however.</span></span> <span data-ttu-id="d0eee-115">例如，使用`System.IO`而不是`System.IOs`。</span><span class="sxs-lookup"><span data-stu-id="d0eee-115">For example, use `System.IO` instead of `System.IOs`.</span></span>  
  
 <span data-ttu-id="d0eee-116">**X DO NOT** 該命名空間中使用相同名稱的命名空間和類型。</span><span class="sxs-lookup"><span data-stu-id="d0eee-116">**X DO NOT** use the same name for a namespace and a type in that namespace.</span></span>  
  
 <span data-ttu-id="d0eee-117">例如，請勿使用`Debug`的命名空間名稱，並也提供類別，名為`Debug`相同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="d0eee-117">For example, do not use `Debug` as a namespace name and then also provide a class named `Debug` in the same namespace.</span></span> <span data-ttu-id="d0eee-118">有好幾種編譯器需要這類的類型是完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d0eee-118">Several compilers require such types to be fully qualified.</span></span>  
  
### <a name="namespaces-and-type-name-conflicts"></a><span data-ttu-id="d0eee-119">命名空間和類型名稱衝突</span><span class="sxs-lookup"><span data-stu-id="d0eee-119">Namespaces and Type Name Conflicts</span></span>  
 <span data-ttu-id="d0eee-120">**X DO NOT** 引入泛型型別名稱，例如 `Element`， `Node`， `Log`，和 `Message`。</span><span class="sxs-lookup"><span data-stu-id="d0eee-120">**X DO NOT** introduce generic type names such as `Element`, `Node`, `Log`, and `Message`.</span></span>  
  
 <span data-ttu-id="d0eee-121">沒有極高的可能這樣做會導致輸入名稱衝突在一般案例。</span><span class="sxs-lookup"><span data-stu-id="d0eee-121">There is a very high probability that doing so will lead to type name conflicts in common scenarios.</span></span> <span data-ttu-id="d0eee-122">您應該符合資格的泛型型別名稱 (`FormElement`， `XmlNode`， `EventLog`， `SoapMessage`)。</span><span class="sxs-lookup"><span data-stu-id="d0eee-122">You should qualify the generic type names (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).</span></span>  
  
 <span data-ttu-id="d0eee-123">有避免不同類別的命名空間的型別名稱衝突的特定方針。</span><span class="sxs-lookup"><span data-stu-id="d0eee-123">There are specific guidelines for avoiding type name conflicts for different categories of namespaces.</span></span>  
  
-   <span data-ttu-id="d0eee-124">**應用程式模型命名空間**</span><span class="sxs-lookup"><span data-stu-id="d0eee-124">**Application model namespaces**</span></span>  
  
     <span data-ttu-id="d0eee-125">屬於單一應用程式模型的命名空間會經常一起使用，但幾乎不會搭配其他應用程式模型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d0eee-125">Namespaces belonging to a single application model are very often used together, but they are almost never used with namespaces of other application models.</span></span> <span data-ttu-id="d0eee-126">例如，<xref:System.Windows.Forms?displayProperty=nameWithType>命名空間很少可搭配使用<xref:System.Web.UI?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="d0eee-126">For example, the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace is very rarely used together with the <xref:System.Web.UI?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d0eee-127">以下是已知的應用程式模型命名空間群組的清單：</span><span class="sxs-lookup"><span data-stu-id="d0eee-127">The following is a list of well-known application model namespace groups:</span></span>  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     <span data-ttu-id="d0eee-128">**X DO NOT** 讓具有相同名稱的單一應用程式模型中的命名空間中的型別。</span><span class="sxs-lookup"><span data-stu-id="d0eee-128">**X DO NOT** give the same name to types in namespaces within a single application model.</span></span>  
  
     <span data-ttu-id="d0eee-129">比方說，不會將名為的型別`Page`要<xref:System.Web.UI.Adapters?displayProperty=nameWithType>命名空間，因為<xref:System.Web.UI?displayProperty=nameWithType>命名空間已經包含名為的型別`Page`。</span><span class="sxs-lookup"><span data-stu-id="d0eee-129">For example, do not add a type named `Page` to the <xref:System.Web.UI.Adapters?displayProperty=nameWithType> namespace, because the <xref:System.Web.UI?displayProperty=nameWithType> namespace already contains a type named `Page`.</span></span>  
  
-   <span data-ttu-id="d0eee-130">**基礎結構命名空間**</span><span class="sxs-lookup"><span data-stu-id="d0eee-130">**Infrastructure namespaces**</span></span>  
  
     <span data-ttu-id="d0eee-131">此群組包含很少的常見的應用程式開發期間匯入的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d0eee-131">This group contains namespaces that are rarely imported during development of common applications.</span></span> <span data-ttu-id="d0eee-132">比方說，`.Design`命名空間主要是用來開發程式工具。</span><span class="sxs-lookup"><span data-stu-id="d0eee-132">For example, `.Design` namespaces are mainly used when developing programming tools.</span></span> <span data-ttu-id="d0eee-133">避免衝突，這些命名空間中的類型並不重要。</span><span class="sxs-lookup"><span data-stu-id="d0eee-133">Avoiding conflicts with types in these namespaces is not critical.</span></span>  
  
-   <span data-ttu-id="d0eee-134">**核心命名空間**</span><span class="sxs-lookup"><span data-stu-id="d0eee-134">**Core namespaces**</span></span>  
  
     <span data-ttu-id="d0eee-135">核心命名空間包含所有`System`命名空間，但不包括應用程式模型的命名空間和基礎結構命名空間。</span><span class="sxs-lookup"><span data-stu-id="d0eee-135">Core namespaces include all `System` namespaces, excluding namespaces of the application models and the Infrastructure namespaces.</span></span> <span data-ttu-id="d0eee-136">包含核心命名空間，其中， `System`， `System.IO`， `System.Xml`，和`System.Net`。</span><span class="sxs-lookup"><span data-stu-id="d0eee-136">Core namespaces include, among others, `System`, `System.IO`, `System.Xml`, and `System.Net`.</span></span>  
  
     <span data-ttu-id="d0eee-137">**X DO NOT** 授與類型的核心命名空間中的任何類型，會發生衝突的名稱。</span><span class="sxs-lookup"><span data-stu-id="d0eee-137">**X DO NOT** give types names that would conflict with any type in the Core namespaces.</span></span>  
  
     <span data-ttu-id="d0eee-138">比方說，永遠不會使用`Stream`做為型別名稱。</span><span class="sxs-lookup"><span data-stu-id="d0eee-138">For example, never use `Stream` as a type name.</span></span> <span data-ttu-id="d0eee-139">它會和衝突<xref:System.IO.Stream?displayProperty=nameWithType>、 相當常用的型別。</span><span class="sxs-lookup"><span data-stu-id="d0eee-139">It would conflict with <xref:System.IO.Stream?displayProperty=nameWithType>, a very commonly used type.</span></span>  
  
-   <span data-ttu-id="d0eee-140">**技術命名空間群組**</span><span class="sxs-lookup"><span data-stu-id="d0eee-140">**Technology namespace groups**</span></span>  
  
     <span data-ttu-id="d0eee-141">這個分類包括具有相同的前兩個命名空間節點的所有命名空間`(<Company>.<Technology>*`)，例如`Microsoft.Build.Utilities`和`Microsoft.Build.Tasks`。</span><span class="sxs-lookup"><span data-stu-id="d0eee-141">This category includes all namespaces with the same first two namespace nodes `(<Company>.<Technology>*`), such as `Microsoft.Build.Utilities` and `Microsoft.Build.Tasks`.</span></span> <span data-ttu-id="d0eee-142">很重要，彼此不衝突類型屬於單一技術。</span><span class="sxs-lookup"><span data-stu-id="d0eee-142">It is important that types belonging to a single technology do not conflict with each other.</span></span>  
  
     <span data-ttu-id="d0eee-143">**X DO NOT** 指派內單一技術的其他類型的型別名稱，以免造成衝突。</span><span class="sxs-lookup"><span data-stu-id="d0eee-143">**X DO NOT** assign type names that would conflict with other types within a single technology.</span></span>  
  
     <span data-ttu-id="d0eee-144">**X DO NOT** （除非該技術不是用於與應用程式模型） 導入技術的命名空間中的型別和應用程式模型命名空間之間的類型名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="d0eee-144">**X DO NOT** introduce type name conflicts between types in technology namespaces and an application model namespace (unless the technology is not intended to be used with the application model).</span></span>  
  
 <span data-ttu-id="d0eee-145">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="d0eee-145">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d0eee-146">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="d0eee-146">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0eee-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0eee-147">See also</span></span>

- [<span data-ttu-id="d0eee-148">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="d0eee-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="d0eee-149">命名方針</span><span class="sxs-lookup"><span data-stu-id="d0eee-149">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
