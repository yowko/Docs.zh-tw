---
title: 不區分文化特性的字串作業
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ca35f73590f8a7c58a0044136c05f341796dfc
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441654"
---
# <a name="culture-insensitive-string-operations"></a><span data-ttu-id="ad47e-102">不區分文化特性 (Culture) 的字串作業</span><span class="sxs-lookup"><span data-stu-id="ad47e-102">Culture-insensitive string operations</span></span>

<span data-ttu-id="ad47e-103">如果您建立的應用程式會根據個別文化特性對使用者顯示結果，區分文化特性字串作業將有所助益。</span><span class="sxs-lookup"><span data-stu-id="ad47e-103">Culture-sensitive string operations can be an advantage if you are creating applications designed to display results to users on a per-culture basis.</span></span> <span data-ttu-id="ad47e-104">根據預設，區分文化特性的方法會從目前執行緒的 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 屬性取得要使用的文化特性。</span><span class="sxs-lookup"><span data-stu-id="ad47e-104">By default, culture-sensitive methods obtain the culture to use from the <xref:System.Globalization.CultureInfo.CurrentCulture%2A> property for the current thread.</span></span>

<span data-ttu-id="ad47e-105">請注意，區分文化特性的字串作業並不一定是所要的行為。</span><span class="sxs-lookup"><span data-stu-id="ad47e-105">Note that culture-sensitive string operations are not always the desired behavior.</span></span> <span data-ttu-id="ad47e-106">若結果應該與文化特性無關，但使用了區分文化特性的作業，可能會造成應用程式程式碼在具有自訂大小寫對應和排序規則的文化特性上失敗。</span><span class="sxs-lookup"><span data-stu-id="ad47e-106">Using culture-sensitive operations when results should be independent of culture can cause application code to fail on cultures with custom case mappings and sorting rules.</span></span> <span data-ttu-id="ad47e-107">如需範例，請參閱[使用字串的最佳做法](../../../docs/standard/base-types/best-practices-strings.md)一文中的[使用目前文化特性 (Culture) 的字串比較](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture)一節。</span><span class="sxs-lookup"><span data-stu-id="ad47e-107">For an example, see the ["String Comparisons that Use the Current Culture"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) section in the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article.</span></span>

<span data-ttu-id="ad47e-108">字串作業是否應該區分文化特性取決於您的應用程式如何使用結果。</span><span class="sxs-lookup"><span data-stu-id="ad47e-108">Whether string operations should be culture-sensitive or culture-insensitive depends on how your application uses the results.</span></span> <span data-ttu-id="ad47e-109">對使用者顯示結果的字串作業，通常都是區分文化特性的。</span><span class="sxs-lookup"><span data-stu-id="ad47e-109">String operations that display results to the user should typically be culture-sensitive.</span></span> <span data-ttu-id="ad47e-110">例如，如果應用程式要在清單方塊中顯示排序過的當地語系化字串清單，應用程式就應該執行區分文化特性的排序。</span><span class="sxs-lookup"><span data-stu-id="ad47e-110">For example, if an application displays a sorted list of localized strings in a list box, the application should perform a culture-sensitive sort.</span></span>

<span data-ttu-id="ad47e-111">用於內部的字串作業的結果，通常都是不區分文化特性的。</span><span class="sxs-lookup"><span data-stu-id="ad47e-111">Results of string operations that are used internally should typically be culture-insensitive.</span></span> <span data-ttu-id="ad47e-112">一般而言，如果應用程式使用沒有對使用者顯示的檔名、保存性格式或符號資訊，字串作業的結果便不應該因文化特性而有所不同。</span><span class="sxs-lookup"><span data-stu-id="ad47e-112">In general, if the application is working with file names, persistence formats, or symbolic information that is not displayed to the user, results of string operations should not vary by culture.</span></span> <span data-ttu-id="ad47e-113">例如，如果應用程式進行字串的比較，以判斷該字串是否為可以辨認的 XML 標記，則這項比較就不應是區分文化特性的。</span><span class="sxs-lookup"><span data-stu-id="ad47e-113">For example, if an application compares a string to determine whether it is a recognized XML tag, the comparison should not be culture-sensitive.</span></span> <span data-ttu-id="ad47e-114">此外，如果安全性決策必須依據字串比較的結果進行，則作業應該不區分文化特性，以確保結果不受 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 的值影響。</span><span class="sxs-lookup"><span data-stu-id="ad47e-114">In addition, if a security decision is based on the result of a string comparison or case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span></span>

<span data-ttu-id="ad47e-115">不論您是否要開發含有處理當地語系化和全球化問題之程式碼的應用程式，您應該知道預設情況下會擷取區分文化特性結果的 .NET Framework 方法。</span><span class="sxs-lookup"><span data-stu-id="ad47e-115">Whether or not you are developing an application that includes code to handle localization and globalization issues, you should be aware of the .NET Framework methods that retrieve culture-sensitive results by default.</span></span> <span data-ttu-id="ad47e-116">本主題的目的在說明當您的應用程式想要取得不區分文化特性的結果時，使用這些方法的正確方式。</span><span class="sxs-lookup"><span data-stu-id="ad47e-116">The purpose of this topic is to illustrate the correct way for your applications to use these methods to obtain culture-insensitive results.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad47e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad47e-117">See also</span></span>

- [<span data-ttu-id="ad47e-118">全球化和當地語系化</span><span class="sxs-lookup"><span data-stu-id="ad47e-118">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
