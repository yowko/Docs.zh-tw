---
title: 執行不區分文化特性的字串比較
ms.date: 08/22/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.CompareTo method
- String.Compare method
- string comparison [.NET Framework], culture-insensitive
- strings [.NET Framework], comparing
- culture-insensitive string operations, comparisons
- culture parameter
ms.assetid: abae50ef-32f7-4a50-a540-fd256fd1aed0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d20ce0f09309c84dcbeb016e0f17c37fe338dd9c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504089"
---
# <a name="performing-culture-insensitive-string-comparisons"></a><span data-ttu-id="3effe-102">執行不區分文化特性的字串比較</span><span class="sxs-lookup"><span data-stu-id="3effe-102">Performing Culture-Insensitive String Comparisons</span></span>
<span data-ttu-id="3effe-103">根據預設，<xref:System.String.Compare%2A?displayProperty=nameWithType> 方法會執行區分文化特性和區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="3effe-103">By default, the <xref:System.String.Compare%2A?displayProperty=nameWithType> method performs culture-sensitive and case-sensitive comparisons.</span></span> <span data-ttu-id="3effe-104">這個方法也包含幾個多載，這些多載會提供 `culture` 參數 (讓您指定要使用的文化特性) 及 `comparisonType` 參數 (讓您指定要使用的比較規則)。</span><span class="sxs-lookup"><span data-stu-id="3effe-104">This method also includes several overloads that provide a `culture` parameter that lets you specify the culture to use, and a `comparisonType` parameter that lets you specify the comparison rules to use.</span></span> <span data-ttu-id="3effe-105">呼叫這些方法 (而不是預設多載) 會消除有關特定方法呼叫中使用之規則的任何模稜兩可情況，而且可以釐清特定比較是否區分文化特性。</span><span class="sxs-lookup"><span data-stu-id="3effe-105">Calling these methods instead of the default overload removes any ambiguity about the rules used in a particular method call, and makes it clear whether a particular comparison is culture-sensitive or culture-insensitive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3effe-106"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> 方法的兩個多載都會執行區分文化特性和區分大小寫的比較，您不能使用這個方法來執行不區分文化特性的比較。</span><span class="sxs-lookup"><span data-stu-id="3effe-106">Both overloads of the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method perform culture-sensitive and case-sensitive comparisons; you cannot use this method to perform culture-insensitive comparisons.</span></span> <span data-ttu-id="3effe-107">為了讓程式碼更清楚，我們建議您改用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="3effe-107">For code clarity, we recommend that you use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method instead.</span></span>  
  
 <span data-ttu-id="3effe-108">若要進行區分文化特性作業，請指定 <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> 或 <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 列舉值當做 `comparisonType` 參數。</span><span class="sxs-lookup"><span data-stu-id="3effe-108">For culture-sensitive operations, specify the <xref:System.StringComparison.CurrentCulture?displayProperty=nameWithType> or <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enumeration value as the `comparisonType` parameter.</span></span> <span data-ttu-id="3effe-109">如果您想要使用目前文化特性以外的指定文化特性來執行區分文化特性的比較，請指定代表該文化特性的 <xref:System.Globalization.CultureInfo> 物件當做 `culture` 參數。</span><span class="sxs-lookup"><span data-stu-id="3effe-109">If you want to perform a culture-sensitive comparison using a designated culture other than the current culture, specify the <xref:System.Globalization.CultureInfo> object that represents that culture as the `culture` parameter.</span></span>  
  
 <span data-ttu-id="3effe-110"><xref:System.String.Compare%2A?displayProperty=nameWithType> 方法支援的不區分文化特性的字串比較為語言式 (根據不因國別而異的文化特性排序慣例) 或是非語言式 (根據字串中字元的序數值)。</span><span class="sxs-lookup"><span data-stu-id="3effe-110">The culture-insensitive string comparisons supported by the <xref:System.String.Compare%2A?displayProperty=nameWithType> method are either linguistic (based on the sorting conventions of the invariant culture) or non-linguistic (based on the ordinal value of the characters in the string).</span></span> <span data-ttu-id="3effe-111">大多數不區分文化特性的字串比較都是非語言式。</span><span class="sxs-lookup"><span data-stu-id="3effe-111">Most culture-insensitive string comparisons are non-linguistic.</span></span> <span data-ttu-id="3effe-112">若要進行這些比較，請指定 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 或 <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> 列舉值當做 `comparisonType` 參數。</span><span class="sxs-lookup"><span data-stu-id="3effe-112">For these comparisons, specify the <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> or <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> enumeration value as the `comparisonType` parameter.</span></span> <span data-ttu-id="3effe-113">例如，如果安全性決策 (例如使用者名稱或密碼比較) 是依據字串比較的結果，此作業應該不區分文化特性而且為非語言式，以確保結果不受特定文化特性或語言的慣例所影響 </span><span class="sxs-lookup"><span data-stu-id="3effe-113">For example, if a security decision (such as a user name or password comparison) is based on the result of a string comparison, the operation should be culture-insensitive and non-linguistic to ensure that the result is not affected by the conventions of a particular culture or language.</span></span>  
  
 <span data-ttu-id="3effe-114">如果您想要以一致的方式處理多個文化特性中語言相關的字串，請使用不區分文化特性的語言字串比較。</span><span class="sxs-lookup"><span data-stu-id="3effe-114">Use culture-insensitive linguistic string comparison if you want to handle linguistically relevant strings from multiple cultures in a consistent way.</span></span> <span data-ttu-id="3effe-115">例如，如果應用程式顯示的字詞會使用清單方塊中的多個字元集，您可能會想要以相同的順序顯示字詞，不論目前的文化特性為何。</span><span class="sxs-lookup"><span data-stu-id="3effe-115">For example, if your application displays words that use multiple character sets in a list box, you might want to display words in the same order regardless of the current culture.</span></span> <span data-ttu-id="3effe-116">如果是不區分文化特性的語言比較，.NET Framework 會定義以英文語言慣例為基礎的不因國別而異的文化特性。</span><span class="sxs-lookup"><span data-stu-id="3effe-116">For culture-insensitive linguistic comparisons, the .NET Framework defines an invariant culture that is based on the linguistic conventions of English.</span></span> <span data-ttu-id="3effe-117">若要執行不區分文化特性的語言作業，請指定 <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> 或 <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> 當做 `comparisonType` 參數。</span><span class="sxs-lookup"><span data-stu-id="3effe-117">To perform a culture-insensitive linguistic comparison, specify <xref:System.StringComparison.InvariantCulture?displayProperty=nameWithType> or <xref:System.StringComparison.InvariantCultureIgnoreCase?displayProperty=nameWithType> as the `comparisonType` parameter.</span></span>  
  
 <span data-ttu-id="3effe-118">下列範例執行兩個不區分文化特性的非語言式字串比較。</span><span class="sxs-lookup"><span data-stu-id="3effe-118">The following example performs two culture-insensitive, non-linguistic string comparisons.</span></span> <span data-ttu-id="3effe-119">第一個比較區分大小寫，第二個比較則不區分。</span><span class="sxs-lookup"><span data-stu-id="3effe-119">The first is case-sensitive, but the second is not.</span></span>  
  
 [!code-csharp[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/cs/cultureinsensitive1.cs#1)]
 [!code-vb[Conceptual.Strings.CultureInsensitiveComparison#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.strings.cultureinsensitivecomparison/vb/cultureinsensitive1.vb#1)]  

<span data-ttu-id="3effe-120">您可以下載[排序權數資料表](https://www.microsoft.com/en-us/download/details.aspx?id=10921)，該文字檔集合包含在 Windows 作業系統排序及比較作業中使用的字元權數資訊，以及下載[預設 Unicode 定序元素資料表](https://www.unicode.org/Public/UCA/latest/allkeys.txt) (適用於 Linux 和 macOS 的排序權數資料表)。</span><span class="sxs-lookup"><span data-stu-id="3effe-120">You can download the [Sorting Weight Tables](https://www.microsoft.com/en-us/download/details.aspx?id=10921), a set of text files that contain information on the character weights used in sorting and comparison operations for Windows operating systems, and the [Default Unicode Collation Element Table](https://www.unicode.org/Public/UCA/latest/allkeys.txt), the sort weight table for Linux and macOS.</span></span>

## <a name="see-also"></a><span data-ttu-id="3effe-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3effe-121">See also</span></span>

- <xref:System.String.Compare%2A?displayProperty=nameWithType>
- <xref:System.String.CompareTo%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3effe-122">執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="3effe-122">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
- [<span data-ttu-id="3effe-123">使用字串的最佳做法</span><span class="sxs-lookup"><span data-stu-id="3effe-123">Best Practices for Using Strings</span></span>](../../../docs/standard/base-types/best-practices-strings.md)
