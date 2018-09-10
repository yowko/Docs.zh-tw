---
title: 執行不區分文化特性的大小寫變更
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 844b0edb93b93704c4886495c673dc0496f7ba71
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44192973"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="68448-102">執行不區分文化特性的大小寫變更</span><span class="sxs-lookup"><span data-stu-id="68448-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="68448-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType> 和 <xref:System.Char.ToLower%2A?displayProperty=nameWithType> 方法提供不接受任何參數的多載。</span><span class="sxs-lookup"><span data-stu-id="68448-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="68448-104">根據預設，不含參數的這些多載會根據 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 的值，執行大小寫變更。</span><span class="sxs-lookup"><span data-stu-id="68448-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="68448-105">這會產生可能會因為文化特性而有所不同的區分大小寫結果。</span><span class="sxs-lookup"><span data-stu-id="68448-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="68448-106">若要釐清您希望大小寫變更是區分文化特性還是不區分文化特性，就應該使用要求您明確地指定 `culture` 參數的這些方法的多載。</span><span class="sxs-lookup"><span data-stu-id="68448-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="68448-107">針對區分文化特性的大小寫變更，請為 `culture` 參數指定 `CultureInfo.CurrentCulture`。</span><span class="sxs-lookup"><span data-stu-id="68448-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="68448-108">至於不區分文化特性的大小寫變更，則為 `culture` 參數指定 `CultureInfo.InvariantCulture`。</span><span class="sxs-lookup"><span data-stu-id="68448-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="68448-109">字串通常會轉換為標準大小寫，讓之後能夠更輕鬆地查閱。</span><span class="sxs-lookup"><span data-stu-id="68448-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="68448-110">以這種方式使用字串時，您應該為 `culture` 參數指定 `CultureInfo.InvariantCulture`，因為 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 的值在變更大小寫的時間與發生查閱的時間之間可能會有所變更。</span><span class="sxs-lookup"><span data-stu-id="68448-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="68448-111">如果安全性決策必須以大小寫變更作業為基礎，則作業應該不區分文化特性，以確保結果不受 `CultureInfo.CurrentCulture` 的值影響。</span><span class="sxs-lookup"><span data-stu-id="68448-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="68448-112">如需示範區分文化特性的字串作業如何產生不一致結果的範例，請參閱[使用字串的最佳做法](../../../docs/standard/base-types/best-practices-strings.md)一文中的＜使用目前文化特性的字串比較＞一節。</span><span class="sxs-lookup"><span data-stu-id="68448-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="68448-113">使用 String.ToUpper 和 String.ToLower 方法</span><span class="sxs-lookup"><span data-stu-id="68448-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="68448-114">為使程式碼更清楚，建議您務必使用 `String.ToUpper` 和 `String.ToLower` 方法的多載，讓您明確地指定 `culture` 參數。</span><span class="sxs-lookup"><span data-stu-id="68448-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="68448-115">例如，下列程式碼會執行識別碼查閱。</span><span class="sxs-lookup"><span data-stu-id="68448-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="68448-116">`key.ToLower` 作業預設為區分文化特性，但讀取程式碼時，這種行為並不明確。</span><span class="sxs-lookup"><span data-stu-id="68448-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="68448-117">範例</span><span class="sxs-lookup"><span data-stu-id="68448-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="68448-118">如果您希望 `key.ToLower` 作業是不區分文化特性，則應該如下所示變更上述範例，才能在變更大小寫時，明確地使用 `CultureInfo.InvariantCulture`。</span><span class="sxs-lookup"><span data-stu-id="68448-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="68448-119">使用 Char.ToUpper 和 Char.ToLower 方法</span><span class="sxs-lookup"><span data-stu-id="68448-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="68448-120">雖然 `Char.ToUpper` 和 `Char.ToLower` 方法具有與 `String.ToUpper` 和 `String.ToLower` 方法相同的特性，但是受到影響的文化特性只有土耳其文 (土耳其) 和亞塞拜然文 (拉丁，亞塞拜然)。</span><span class="sxs-lookup"><span data-stu-id="68448-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="68448-121">這些是具有單一字元大小寫差異的唯二文化特性。</span><span class="sxs-lookup"><span data-stu-id="68448-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="68448-122">如需這個特殊案例對應的詳細資訊，請參閱 <xref:System.String> 類別主題中的＜大小寫＞一節。</span><span class="sxs-lookup"><span data-stu-id="68448-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="68448-123">為使程式碼更清楚並確保一致性的結果，建議您務必使用這些方法的多載，讓您明確地指定 `culture` 參數。</span><span class="sxs-lookup"><span data-stu-id="68448-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68448-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68448-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="68448-125">執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="68448-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
