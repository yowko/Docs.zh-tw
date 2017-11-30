---
title: "執行不區分文化特性的大小寫變更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="8da08-102">執行不區分文化特性的大小寫變更</span><span class="sxs-lookup"><span data-stu-id="8da08-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="8da08-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>， <xref:System.String.ToLower%2A?displayProperty=nameWithType>， <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>，和<xref:System.Char.ToLower%2A?displayProperty=nameWithType>方法提供不接受任何參數的多載。</span><span class="sxs-lookup"><span data-stu-id="8da08-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="8da08-104">根據預設，不含參數的這些多載會執行大小寫變更的值為基礎<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="8da08-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8da08-105">這會產生區分大小寫可能會因文化特性的結果。</span><span class="sxs-lookup"><span data-stu-id="8da08-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="8da08-106">若要清除您是否想要區分文化特性或不區分文化特性的大小寫變更，您應該使用這些方法需要您明確指定的多載`culture`參數。</span><span class="sxs-lookup"><span data-stu-id="8da08-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="8da08-107">對於區分文化特性大小寫變更，指定`CultureInfo.CurrentCulture`如`culture`參數。</span><span class="sxs-lookup"><span data-stu-id="8da08-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="8da08-108">不區分文化特性的大小寫變更為指定`CultureInfo.InvariantCulture`如`culture`參數。</span><span class="sxs-lookup"><span data-stu-id="8da08-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="8da08-109">通常，字串會轉換至標準案例，以更新版本可讓您更輕鬆查閱。</span><span class="sxs-lookup"><span data-stu-id="8da08-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="8da08-110">當以這種方式使用字串時，您應該指定`CultureInfo.InvariantCulture`如`culture`參數，因為值<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>有可能變更大小寫變更的時間之間的查閱，就會發生的時間。</span><span class="sxs-lookup"><span data-stu-id="8da08-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="8da08-111">如果安全性決策根據大小寫變更作業，應該不區分文化特性以確保結果的值不會影響作業`CultureInfo.CurrentCulture`。</span><span class="sxs-lookup"><span data-stu-id="8da08-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="8da08-112">請參閱 「 字串比較，使用目前文化特性 」 一節[使用字串的最佳作法](../../../docs/standard/base-types/best-practices-strings.md)文件的範例示範如何區分文化特性字串作業可能會產生不一致的結果。</span><span class="sxs-lookup"><span data-stu-id="8da08-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="8da08-113">使用 String.ToUpper 和 String.ToLower 方法</span><span class="sxs-lookup"><span data-stu-id="8da08-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="8da08-114">程式碼更清楚，所以，建議您一定要使用的多載`String.ToUpper`和`String.ToLower`方法可讓您指定`culture`參數明確。</span><span class="sxs-lookup"><span data-stu-id="8da08-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="8da08-115">例如，下列程式碼會執行識別項查詢。</span><span class="sxs-lookup"><span data-stu-id="8da08-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="8da08-116">`key.ToLower`作業是區分文化特性的預設值，但這種行為並不清楚，無法讀取程式碼。</span><span class="sxs-lookup"><span data-stu-id="8da08-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="8da08-117">範例</span><span class="sxs-lookup"><span data-stu-id="8da08-117">Example</span></span>  
  
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
  
 <span data-ttu-id="8da08-118">如果您想`key.ToLower`作業是不區分文化特性，您應該變更上述範例，如下所示，以明確地使用`CultureInfo.InvariantCulture`時變更大小寫。</span><span class="sxs-lookup"><span data-stu-id="8da08-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="8da08-119">使用 Char.ToUpper 和 Char.ToLower 方法</span><span class="sxs-lookup"><span data-stu-id="8da08-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="8da08-120">雖然`Char.ToUpper`和`Char.ToLower`方法有相同的特性`String.ToUpper`和`String.ToLower`方法，只會受到影響的文化特性為土耳其文 （土耳其） 和亞塞拜然 （拉丁文，亞塞拜然）。</span><span class="sxs-lookup"><span data-stu-id="8da08-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="8da08-121">這些是只有兩個文化特性而有所不同，但單一字元大小寫的差異。</span><span class="sxs-lookup"><span data-stu-id="8da08-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="8da08-122">如需這個特殊案例對應的詳細資訊，請參閱 <xref:System.String> 類別主題中的＜大小寫＞一節。</span><span class="sxs-lookup"><span data-stu-id="8da08-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="8da08-123">程式碼更清楚，所以，並確保一致的結果，建議您一律使用這些方法可讓您明確指定的多載`culture`參數。</span><span class="sxs-lookup"><span data-stu-id="8da08-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da08-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8da08-124">See Also</span></span>  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8da08-125">執行不區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="8da08-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
