---
title: 大小寫慣例
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 070fc69728c2cb38e465dab9f6f591a77a857531
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703222"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="ca75f-102">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="ca75f-102">Capitalization Conventions</span></span>
<span data-ttu-id="ca75f-103">簡單的方法，使用這一章配置中的指導方針情況下，當套用一致的方式，請識別項型別、 成員和參數容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="ca75f-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="ca75f-104">識別項的大小寫規則</span><span class="sxs-lookup"><span data-stu-id="ca75f-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="ca75f-105">若要區分識別項中的文字，利用識別項中的每個單字的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="ca75f-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="ca75f-106">請勿使用底線來區分文字，或就此而言，在識別項中任何位置。</span><span class="sxs-lookup"><span data-stu-id="ca75f-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="ca75f-107">有兩個適當的方法，可以改為大寫識別碼，根據所使用的識別項：</span><span class="sxs-lookup"><span data-stu-id="ca75f-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
-   <span data-ttu-id="ca75f-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="ca75f-108">PascalCasing</span></span>  
  
-   <span data-ttu-id="ca75f-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="ca75f-109">camelCasing</span></span>  
  
 <span data-ttu-id="ca75f-110">參數名稱除外的所有識別項所使用的 PascalCasing 慣例轉換成大寫字母 （包括透過長度的兩個字母的縮寫） 的每個字的第一個字元，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ca75f-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="ca75f-111">特殊案例是進行中這兩個字母大寫，兩個字母縮寫，下列識別碼中所示：</span><span class="sxs-lookup"><span data-stu-id="ca75f-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="ca75f-112">CamelCasing 慣例，參數名稱，僅用於轉換成大寫字母的第一個字，除了每個單字的第一個字元，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ca75f-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="ca75f-113">因為此範例也示範，開始使用依照 camel 命名法大小寫的識別項的兩個字母縮略字都是小寫。</span><span class="sxs-lookup"><span data-stu-id="ca75f-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="ca75f-114">**✓ 請** 為所有由多個單字所組成的公用成員、 類型和命名空間名稱使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="ca75f-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="ca75f-115">**✓ 請** 為參數名稱使用 camelCasing。  </span><span class="sxs-lookup"><span data-stu-id="ca75f-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="ca75f-116">下表描述不同類型的識別項的大小寫規則。</span><span class="sxs-lookup"><span data-stu-id="ca75f-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="ca75f-117">識別項</span><span class="sxs-lookup"><span data-stu-id="ca75f-117">Identifier</span></span>|<span data-ttu-id="ca75f-118">大小寫</span><span class="sxs-lookup"><span data-stu-id="ca75f-118">Casing</span></span>|<span data-ttu-id="ca75f-119">範例</span><span class="sxs-lookup"><span data-stu-id="ca75f-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="ca75f-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="ca75f-120">Namespace</span></span>|<span data-ttu-id="ca75f-121">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="ca75f-122">類型</span><span class="sxs-lookup"><span data-stu-id="ca75f-122">Type</span></span>|<span data-ttu-id="ca75f-123">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="ca75f-124">介面</span><span class="sxs-lookup"><span data-stu-id="ca75f-124">Interface</span></span>|<span data-ttu-id="ca75f-125">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="ca75f-126">方法</span><span class="sxs-lookup"><span data-stu-id="ca75f-126">Method</span></span>|<span data-ttu-id="ca75f-127">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="ca75f-128">屬性</span><span class="sxs-lookup"><span data-stu-id="ca75f-128">Property</span></span>|<span data-ttu-id="ca75f-129">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="ca75f-130">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="ca75f-130">Event</span></span>|<span data-ttu-id="ca75f-131">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="ca75f-132">欄位</span><span class="sxs-lookup"><span data-stu-id="ca75f-132">Field</span></span>|<span data-ttu-id="ca75f-133">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="ca75f-134">列舉值</span><span class="sxs-lookup"><span data-stu-id="ca75f-134">Enum value</span></span>|<span data-ttu-id="ca75f-135">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="ca75f-136">參數</span><span class="sxs-lookup"><span data-stu-id="ca75f-136">Parameter</span></span>|<span data-ttu-id="ca75f-137">依照 camel 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="ca75f-138">大寫的複合字和一般詞彙</span><span class="sxs-lookup"><span data-stu-id="ca75f-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="ca75f-139">大部分的複合詞彙會被視為單一字詞大小寫的目的。</span><span class="sxs-lookup"><span data-stu-id="ca75f-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="ca75f-140">**X DO NOT** 所謂的封閉式複合字組中的每個字大寫。</span><span class="sxs-lookup"><span data-stu-id="ca75f-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="ca75f-141">這些是寫成單字，例如端點的複合字。</span><span class="sxs-lookup"><span data-stu-id="ca75f-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="ca75f-142">大小寫的指導方針，以將關閉表單的複合字視為單一的文字。</span><span class="sxs-lookup"><span data-stu-id="ca75f-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="ca75f-143">使用目前的字典來判斷複合字以關閉表單。</span><span class="sxs-lookup"><span data-stu-id="ca75f-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="ca75f-144">Pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-144">Pascal</span></span>|<span data-ttu-id="ca75f-145">依照 camel 命名法</span><span class="sxs-lookup"><span data-stu-id="ca75f-145">Camel</span></span>|<span data-ttu-id="ca75f-146">not</span><span class="sxs-lookup"><span data-stu-id="ca75f-146">Not</span></span>|  
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
  
## <a name="case-sensitivity"></a><span data-ttu-id="ca75f-147">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="ca75f-147">Case Sensitivity</span></span>  
 <span data-ttu-id="ca75f-148">雖然有些可以在 CLR 執行的語言不需要支援區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ca75f-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="ca75f-149">即使您的語言支援，可能會存取您的架構的其他語言則否。</span><span class="sxs-lookup"><span data-stu-id="ca75f-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="ca75f-150">任何 Api，從外部存取，因此，不能依賴來區別兩個名稱相同的內容中的案例。</span><span class="sxs-lookup"><span data-stu-id="ca75f-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="ca75f-151">**X DO NOT** 假設所有的程式語言不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ca75f-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="ca75f-152">但它們並不相等。</span><span class="sxs-lookup"><span data-stu-id="ca75f-152">They are not.</span></span> <span data-ttu-id="ca75f-153">名稱不能單獨的大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="ca75f-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="ca75f-154">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="ca75f-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ca75f-155">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="ca75f-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca75f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca75f-156">See also</span></span>

- [<span data-ttu-id="ca75f-157">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="ca75f-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="ca75f-158">命名方針</span><span class="sxs-lookup"><span data-stu-id="ca75f-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
