---
title: 大小寫慣例
description: 針對識別碼、複合字和共同詞彙套用大小寫慣例。 瞭解在 .NET 中區分大小寫的運作方式。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 4903dc587d84ef36bfaa641cfbda59484266c23c
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84767789"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="94c02-104">大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="94c02-104">Capitalization Conventions</span></span>
<span data-ttu-id="94c02-105">本章中的指導方針會配置一個簡單的方法，以便在一致地套用時，讓型別、成員和參數的識別碼易於閱讀。</span><span class="sxs-lookup"><span data-stu-id="94c02-105">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="94c02-106">識別碼的大小寫規則</span><span class="sxs-lookup"><span data-stu-id="94c02-106">Capitalization Rules for Identifiers</span></span>
 <span data-ttu-id="94c02-107">若要區分識別碼中的單字，請將識別碼中每個單字的第一個字母大寫。</span><span class="sxs-lookup"><span data-stu-id="94c02-107">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="94c02-108">請不要使用底線來區別單字，或在識別碼中的任何位置區分。</span><span class="sxs-lookup"><span data-stu-id="94c02-108">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="94c02-109">有兩個適當的方式可將識別碼大寫，視使用識別碼而定：</span><span class="sxs-lookup"><span data-stu-id="94c02-109">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="94c02-110">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="94c02-110">PascalCasing</span></span>

- <span data-ttu-id="94c02-111">camelCasing</span><span class="sxs-lookup"><span data-stu-id="94c02-111">camelCasing</span></span>

 <span data-ttu-id="94c02-112">PascalCasing 慣例，用於參數名稱以外的所有識別碼，會將每個字組的第一個字元（包含長度超過兩個字母的縮寫）設為大寫，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="94c02-112">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="94c02-113">特殊案例是針對兩個字母的縮寫，其中兩個字母都是大寫，如下列識別碼所示：</span><span class="sxs-lookup"><span data-stu-id="94c02-113">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="94c02-114">CamelCasing 慣例僅用於參數名稱，會將每個字組的第一個字元設為大寫，但第一個單字除外，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="94c02-114">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="94c02-115">如範例所示，開始使用 camel 大小寫識別碼的兩個字母縮略字，兩者都是小寫。</span><span class="sxs-lookup"><span data-stu-id="94c02-115">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="94c02-116">✔️對於所有包含多個單字的公用成員、類型和命名空間名稱，請使用 PascalCasing。</span><span class="sxs-lookup"><span data-stu-id="94c02-116">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="94c02-117">✔️請對參數名稱使用 camelCasing。</span><span class="sxs-lookup"><span data-stu-id="94c02-117">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="94c02-118">下表描述不同識別碼類型的大小寫規則。</span><span class="sxs-lookup"><span data-stu-id="94c02-118">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="94c02-119">識別碼</span><span class="sxs-lookup"><span data-stu-id="94c02-119">Identifier</span></span>|<span data-ttu-id="94c02-120">大小寫</span><span class="sxs-lookup"><span data-stu-id="94c02-120">Casing</span></span>|<span data-ttu-id="94c02-121">範例</span><span class="sxs-lookup"><span data-stu-id="94c02-121">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="94c02-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="94c02-122">Namespace</span></span>|<span data-ttu-id="94c02-123">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-123">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="94c02-124">類型</span><span class="sxs-lookup"><span data-stu-id="94c02-124">Type</span></span>|<span data-ttu-id="94c02-125">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-125">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="94c02-126">介面</span><span class="sxs-lookup"><span data-stu-id="94c02-126">Interface</span></span>|<span data-ttu-id="94c02-127">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-127">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="94c02-128">方法</span><span class="sxs-lookup"><span data-stu-id="94c02-128">Method</span></span>|<span data-ttu-id="94c02-129">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-129">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="94c02-130">屬性</span><span class="sxs-lookup"><span data-stu-id="94c02-130">Property</span></span>|<span data-ttu-id="94c02-131">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-131">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="94c02-132">事件</span><span class="sxs-lookup"><span data-stu-id="94c02-132">Event</span></span>|<span data-ttu-id="94c02-133">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-133">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="94c02-134">欄位</span><span class="sxs-lookup"><span data-stu-id="94c02-134">Field</span></span>|<span data-ttu-id="94c02-135">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-135">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="94c02-136">列舉值</span><span class="sxs-lookup"><span data-stu-id="94c02-136">Enum value</span></span>|<span data-ttu-id="94c02-137">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-137">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="94c02-138">參數</span><span class="sxs-lookup"><span data-stu-id="94c02-138">Parameter</span></span>|<span data-ttu-id="94c02-139">Camel</span><span class="sxs-lookup"><span data-stu-id="94c02-139">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="94c02-140">將複合字和共同詞彙大寫</span><span class="sxs-lookup"><span data-stu-id="94c02-140">Capitalizing Compound Words and Common Terms</span></span>
 <span data-ttu-id="94c02-141">大部分的複合詞匯會視為大寫用途的單一單字。</span><span class="sxs-lookup"><span data-stu-id="94c02-141">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="94c02-142">❌請不要將所謂的封閉表單複合單字中的每個字大寫。</span><span class="sxs-lookup"><span data-stu-id="94c02-142">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="94c02-143">這些是以單一單字撰寫的複合字組，例如端點。</span><span class="sxs-lookup"><span data-stu-id="94c02-143">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="94c02-144">基於大小寫方針的目的，請將封閉形式的複合字視為單一單字。</span><span class="sxs-lookup"><span data-stu-id="94c02-144">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="94c02-145">使用目前的字典來判斷複合字是否以已關閉的形式寫入。</span><span class="sxs-lookup"><span data-stu-id="94c02-145">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="94c02-146">Pascal</span><span class="sxs-lookup"><span data-stu-id="94c02-146">Pascal</span></span>|<span data-ttu-id="94c02-147">Camel</span><span class="sxs-lookup"><span data-stu-id="94c02-147">Camel</span></span>|<span data-ttu-id="94c02-148">Not</span><span class="sxs-lookup"><span data-stu-id="94c02-148">Not</span></span>|
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

## <a name="case-sensitivity"></a><span data-ttu-id="94c02-149">區分大小寫</span><span class="sxs-lookup"><span data-stu-id="94c02-149">Case Sensitivity</span></span>
 <span data-ttu-id="94c02-150">可以在 CLR 上執行的語言並不需要支援區分大小寫，雖然有些也是如此。</span><span class="sxs-lookup"><span data-stu-id="94c02-150">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="94c02-151">即使您的語言支援它，其他可能存取您架構的語言也不會。</span><span class="sxs-lookup"><span data-stu-id="94c02-151">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="94c02-152">因此，可從外部存取的任何 Api 都不能單獨依賴大小寫來區別相同內容中的兩個名稱。</span><span class="sxs-lookup"><span data-stu-id="94c02-152">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="94c02-153">❌請勿假設所有程式設計語言都區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="94c02-153">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="94c02-154">但它們並不相等。</span><span class="sxs-lookup"><span data-stu-id="94c02-154">They are not.</span></span> <span data-ttu-id="94c02-155">名稱不能單獨以大小寫不同。</span><span class="sxs-lookup"><span data-stu-id="94c02-155">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="94c02-156">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="94c02-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="94c02-157">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="94c02-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="94c02-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94c02-158">See also</span></span>

- [<span data-ttu-id="94c02-159">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="94c02-159">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="94c02-160">命名方針</span><span class="sxs-lookup"><span data-stu-id="94c02-160">Naming Guidelines</span></span>](naming-guidelines.md)
