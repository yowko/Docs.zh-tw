---
title: "大小寫慣例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1bddb7bb3559e6f39b7884b92f64bee8fbb3510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="capitalization-conventions"></a><span data-ttu-id="7f95c-102">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="7f95c-102">Capitalization Conventions</span></span>
<span data-ttu-id="7f95c-103">簡單的方法，使用這個章節配置中的指導方針情況下，當套用一致的方式，請識別項的類型、 成員和參數容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="7f95c-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="7f95c-104">識別項的大小寫規則</span><span class="sxs-lookup"><span data-stu-id="7f95c-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="7f95c-105">若要區分識別項中的文字，將變成大寫識別項中的每個單字的第一個的字母。</span><span class="sxs-lookup"><span data-stu-id="7f95c-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="7f95c-106">請勿使用底線來區分文字，或該項目的，識別項中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="7f95c-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="7f95c-107">有兩個適當的方法可以改為大寫的識別項，根據所使用的識別項：</span><span class="sxs-lookup"><span data-stu-id="7f95c-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="7f95c-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="7f95c-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="7f95c-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="7f95c-109">camelCasing</span></span>  
  
 <span data-ttu-id="7f95c-110">PascalCasing 慣例使用於所有的識別項，除了參數名稱轉換成大寫字母 （包括透過長度的兩個字母的首字母縮略字） 的每個單字的第一個字元，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7f95c-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="7f95c-111">特殊案例對兩個字母縮略字，這兩個字母都大寫，如下列的識別項中所示：</span><span class="sxs-lookup"><span data-stu-id="7f95c-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="7f95c-112">CamelCasing 慣例，只能用於參數名稱轉換成大寫字母的第一個字，除了每個單字的第一個字元，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="7f95c-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="7f95c-113">此範例也示範，因為開始依照 camel 命名法的大小寫慣例的識別項的兩個字母縮略字都是小寫。</span><span class="sxs-lookup"><span data-stu-id="7f95c-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="7f95c-114">**✓ 不要**PascalCasing 所有公用成員、 類型和命名空間名稱使用多個單字所組成。</span><span class="sxs-lookup"><span data-stu-id="7f95c-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="7f95c-115">**✓ 不要**camelCasing 用於參數名稱。</span><span class="sxs-lookup"><span data-stu-id="7f95c-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="7f95c-116">下表說明不同類型的識別項的大小寫規則。</span><span class="sxs-lookup"><span data-stu-id="7f95c-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="7f95c-117">識別項</span><span class="sxs-lookup"><span data-stu-id="7f95c-117">Identifier</span></span>|<span data-ttu-id="7f95c-118">大小寫</span><span class="sxs-lookup"><span data-stu-id="7f95c-118">Casing</span></span>|<span data-ttu-id="7f95c-119">範例</span><span class="sxs-lookup"><span data-stu-id="7f95c-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="7f95c-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="7f95c-120">Namespace</span></span>|<span data-ttu-id="7f95c-121">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="7f95c-122">類型</span><span class="sxs-lookup"><span data-stu-id="7f95c-122">Type</span></span>|<span data-ttu-id="7f95c-123">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="7f95c-124">介面</span><span class="sxs-lookup"><span data-stu-id="7f95c-124">Interface</span></span>|<span data-ttu-id="7f95c-125">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="7f95c-126">方法</span><span class="sxs-lookup"><span data-stu-id="7f95c-126">Method</span></span>|<span data-ttu-id="7f95c-127">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="7f95c-128">屬性</span><span class="sxs-lookup"><span data-stu-id="7f95c-128">Property</span></span>|<span data-ttu-id="7f95c-129">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="7f95c-130">事件</span><span class="sxs-lookup"><span data-stu-id="7f95c-130">Event</span></span>|<span data-ttu-id="7f95c-131">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="7f95c-132">欄位</span><span class="sxs-lookup"><span data-stu-id="7f95c-132">Field</span></span>|<span data-ttu-id="7f95c-133">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="7f95c-134">列舉值</span><span class="sxs-lookup"><span data-stu-id="7f95c-134">Enum value</span></span>|<span data-ttu-id="7f95c-135">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="7f95c-136">參數</span><span class="sxs-lookup"><span data-stu-id="7f95c-136">Parameter</span></span>|<span data-ttu-id="7f95c-137">依照 camel 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="7f95c-138">大寫的複合字和一般詞彙</span><span class="sxs-lookup"><span data-stu-id="7f95c-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="7f95c-139">大部分的複合詞彙會被視為基於大小寫的單字。</span><span class="sxs-lookup"><span data-stu-id="7f95c-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="7f95c-140">**X 不**所謂的封閉式複合字組中的每個字大寫。</span><span class="sxs-lookup"><span data-stu-id="7f95c-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="7f95c-141">這些是寫成單一的文字，例如端點的複合字。</span><span class="sxs-lookup"><span data-stu-id="7f95c-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="7f95c-142">大小寫的指導方針，以便將關閉表單的複合字視為單一文字。</span><span class="sxs-lookup"><span data-stu-id="7f95c-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="7f95c-143">您可以使用目前的字典來判斷複合字以關閉表單。</span><span class="sxs-lookup"><span data-stu-id="7f95c-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="7f95c-144">依照 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-144">Pascal</span></span>|<span data-ttu-id="7f95c-145">依照 camel 命名法</span><span class="sxs-lookup"><span data-stu-id="7f95c-145">Camel</span></span>|<span data-ttu-id="7f95c-146">not</span><span class="sxs-lookup"><span data-stu-id="7f95c-146">Not</span></span>|  
|------------|-----------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## <a name="case-sensitivity"></a><span data-ttu-id="7f95c-147">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="7f95c-147">Case Sensitivity</span></span>  
 <span data-ttu-id="7f95c-148">可以在 CLR 執行的語言不需要支援區分大小寫，雖然有些執行。</span><span class="sxs-lookup"><span data-stu-id="7f95c-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="7f95c-149">即使您的語言支援，就可能存取您的架構的其他語言則否。</span><span class="sxs-lookup"><span data-stu-id="7f95c-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="7f95c-150">任何應用程式開發介面可外部存取，因此，不能依賴來區別兩個名稱相同的內容中的案例。</span><span class="sxs-lookup"><span data-stu-id="7f95c-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="7f95c-151">**X 不**假設所有的程式語言不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7f95c-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="7f95c-152">但它們並不相等。</span><span class="sxs-lookup"><span data-stu-id="7f95c-152">They are not.</span></span> <span data-ttu-id="7f95c-153">名稱不能單獨的大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="7f95c-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="7f95c-154">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="7f95c-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7f95c-155">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="7f95c-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f95c-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f95c-156">See Also</span></span>  
 [<span data-ttu-id="7f95c-157">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="7f95c-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="7f95c-158">命名方針</span><span class="sxs-lookup"><span data-stu-id="7f95c-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
