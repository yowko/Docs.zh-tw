---
title: 大小寫慣例
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: fee7f5b7749c97a87e37581f67cbe1b49250b9ce
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709526"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="b5d6d-102">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="b5d6d-102">Capitalization Conventions</span></span>
<span data-ttu-id="b5d6d-103">本章中的指導方針會配置一個簡單的方法，以便在一致地套用時，讓型別、成員和參數的識別碼易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-103">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>  
  
## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="b5d6d-104">識別碼的大小寫規則</span><span class="sxs-lookup"><span data-stu-id="b5d6d-104">Capitalization Rules for Identifiers</span></span>  
 <span data-ttu-id="b5d6d-105">若要區分識別碼中的單字，請將識別碼中每個單字的第一個字母大寫。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-105">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="b5d6d-106">請不要使用底線來區別單字，或在識別碼中的任何位置區分。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-106">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="b5d6d-107">有兩個適當的方式可將識別碼大寫，視使用識別碼而定：</span><span class="sxs-lookup"><span data-stu-id="b5d6d-107">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>  
  
- <span data-ttu-id="b5d6d-108">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="b5d6d-108">PascalCasing</span></span>  
  
- <span data-ttu-id="b5d6d-109">camelCasing</span><span class="sxs-lookup"><span data-stu-id="b5d6d-109">camelCasing</span></span>  
  
 <span data-ttu-id="b5d6d-110">PascalCasing 慣例，用於參數名稱以外的所有識別碼，會將每個字組的第一個字元（包含長度超過兩個字母的縮寫）設為大寫，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b5d6d-110">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 <span data-ttu-id="b5d6d-111">特殊案例是針對兩個字母的縮寫，其中兩個字母都是大寫，如下列識別碼所示：</span><span class="sxs-lookup"><span data-stu-id="b5d6d-111">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>  
  
 `IOStream`  
  
 <span data-ttu-id="b5d6d-112">CamelCasing 慣例僅用於參數名稱，會將每個字組的第一個字元設為大寫，但第一個單字除外，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-112">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="b5d6d-113">如範例所示，開始使用 camel 大小寫識別碼的兩個字母縮略字，兩者都是小寫。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-113">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 <span data-ttu-id="b5d6d-114">**✓**會針對所有包含多個單字的公用成員、類型和命名空間名稱使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-114">**✓ DO** use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>  
  
 <span data-ttu-id="b5d6d-115">**✓ DO**使用 camelCasing 做為參數名稱。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-115">**✓ DO** use camelCasing for parameter names.</span></span>  
  
 <span data-ttu-id="b5d6d-116">下表描述不同識別碼類型的大小寫規則。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-116">The following table describes the capitalization rules for different types of identifiers.</span></span>  
  
|<span data-ttu-id="b5d6d-117">識別碼</span><span class="sxs-lookup"><span data-stu-id="b5d6d-117">Identifier</span></span>|<span data-ttu-id="b5d6d-118">大小寫</span><span class="sxs-lookup"><span data-stu-id="b5d6d-118">Casing</span></span>|<span data-ttu-id="b5d6d-119">範例</span><span class="sxs-lookup"><span data-stu-id="b5d6d-119">Example</span></span>|  
|----------------|------------|-------------|  
|<span data-ttu-id="b5d6d-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="b5d6d-120">Namespace</span></span>|<span data-ttu-id="b5d6d-121">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-121">Pascal</span></span>|`namespace System.Security { ... }`|  
|<span data-ttu-id="b5d6d-122">類型</span><span class="sxs-lookup"><span data-stu-id="b5d6d-122">Type</span></span>|<span data-ttu-id="b5d6d-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-123">Pascal</span></span>|`public class StreamReader { ... }`|  
|<span data-ttu-id="b5d6d-124">介面</span><span class="sxs-lookup"><span data-stu-id="b5d6d-124">Interface</span></span>|<span data-ttu-id="b5d6d-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-125">Pascal</span></span>|`public interface IEnumerable { ... }`|  
|<span data-ttu-id="b5d6d-126">方法</span><span class="sxs-lookup"><span data-stu-id="b5d6d-126">Method</span></span>|<span data-ttu-id="b5d6d-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-127">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|<span data-ttu-id="b5d6d-128">屬性</span><span class="sxs-lookup"><span data-stu-id="b5d6d-128">Property</span></span>|<span data-ttu-id="b5d6d-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-129">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|<span data-ttu-id="b5d6d-130">Event</span><span class="sxs-lookup"><span data-stu-id="b5d6d-130">Event</span></span>|<span data-ttu-id="b5d6d-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-131">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|<span data-ttu-id="b5d6d-132">欄位</span><span class="sxs-lookup"><span data-stu-id="b5d6d-132">Field</span></span>|<span data-ttu-id="b5d6d-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-133">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|<span data-ttu-id="b5d6d-134">列舉值</span><span class="sxs-lookup"><span data-stu-id="b5d6d-134">Enum value</span></span>|<span data-ttu-id="b5d6d-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-135">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|<span data-ttu-id="b5d6d-136">參數</span><span class="sxs-lookup"><span data-stu-id="b5d6d-136">Parameter</span></span>|<span data-ttu-id="b5d6d-137">Camel</span><span class="sxs-lookup"><span data-stu-id="b5d6d-137">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="b5d6d-138">將複合字和共同詞彙大寫</span><span class="sxs-lookup"><span data-stu-id="b5d6d-138">Capitalizing Compound Words and Common Terms</span></span>  
 <span data-ttu-id="b5d6d-139">大部分的複合詞匯會視為大寫用途的單一單字。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-139">Most compound terms are treated as single words for purposes of capitalization.</span></span>  
  
 <span data-ttu-id="b5d6d-140">**X 不會**將所謂的封閉表單複合單字中的每個單字全部大寫。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-140">**X DO NOT** capitalize each word in so-called closed-form compound words.</span></span>  
  
 <span data-ttu-id="b5d6d-141">這些是以單一單字撰寫的複合字組，例如端點。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-141">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="b5d6d-142">基於大小寫方針的目的，請將封閉形式的複合字視為單一單字。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-142">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="b5d6d-143">使用目前的字典來判斷複合字是否以已關閉的形式寫入。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-143">Use a current dictionary to determine if a compound word is written in closed form.</span></span>  
  
|<span data-ttu-id="b5d6d-144">Pascal</span><span class="sxs-lookup"><span data-stu-id="b5d6d-144">Pascal</span></span>|<span data-ttu-id="b5d6d-145">Camel</span><span class="sxs-lookup"><span data-stu-id="b5d6d-145">Camel</span></span>|<span data-ttu-id="b5d6d-146">否</span><span class="sxs-lookup"><span data-stu-id="b5d6d-146">Not</span></span>|  
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
  
## <a name="case-sensitivity"></a><span data-ttu-id="b5d6d-147">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="b5d6d-147">Case Sensitivity</span></span>  
 <span data-ttu-id="b5d6d-148">可以在 CLR 上執行的語言並不需要支援區分大小寫，雖然有些也是如此。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-148">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="b5d6d-149">即使您的語言支援它，其他可能存取您架構的語言也不會。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-149">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="b5d6d-150">因此，可從外部存取的任何 Api 都不能單獨依賴大小寫來區別相同內容中的兩個名稱。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-150">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>  
  
 <span data-ttu-id="b5d6d-151">**X**不會假設所有程式設計語言都區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-151">**X DO NOT** assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="b5d6d-152">但它們並不相等。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-152">They are not.</span></span> <span data-ttu-id="b5d6d-153">名稱不能單獨以大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-153">Names cannot differ by case alone.</span></span>  
  
 <span data-ttu-id="b5d6d-154">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="b5d6d-154">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b5d6d-155">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="b5d6d-155">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5d6d-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="b5d6d-156">See also</span></span>

- [<span data-ttu-id="b5d6d-157">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b5d6d-157">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b5d6d-158">命名方針</span><span class="sxs-lookup"><span data-stu-id="b5d6d-158">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
