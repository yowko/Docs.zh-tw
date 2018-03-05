---
title: "如何：使用規則運算式搜尋字串 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="15e61-102">如何：使用規則運算式搜尋字串 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="15e61-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="15e61-103"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 類別可以用來搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="15e61-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="15e61-104">這些搜尋的複雜度範圍可以從非常簡單到充分運用規則運算式。</span><span class="sxs-lookup"><span data-stu-id="15e61-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="15e61-105">以下是使用 <xref:System.Text.RegularExpressions.Regex> 類別搜尋字串的兩個範例。</span><span class="sxs-lookup"><span data-stu-id="15e61-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="15e61-106">如需詳細資訊，請參閱 [.NET Framework 規則運算式](https://msdn.microsoft.com/library/hs600312)。</span><span class="sxs-lookup"><span data-stu-id="15e61-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="15e61-107">範例</span><span class="sxs-lookup"><span data-stu-id="15e61-107">Example</span></span>  
 <span data-ttu-id="15e61-108">下列程式碼是一個主控台應用程式，可對陣列中的字串執行簡單的不區分大小寫搜尋。</span><span class="sxs-lookup"><span data-stu-id="15e61-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="15e61-109"><xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 靜態方法會執行搜尋，該搜尋已指定要搜尋的字串，且字串包含搜尋模式。</span><span class="sxs-lookup"><span data-stu-id="15e61-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="15e61-110">在此情況下，第三個引數用來表示應該忽略大小寫。</span><span class="sxs-lookup"><span data-stu-id="15e61-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="15e61-111">如需詳細資訊，請參閱<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="15e61-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="15e61-112">範例</span><span class="sxs-lookup"><span data-stu-id="15e61-112">Example</span></span>  
 <span data-ttu-id="15e61-113">下列程式碼是主控台應用程式，可使用規則運算式來驗證陣列中每個字串的格式。</span><span class="sxs-lookup"><span data-stu-id="15e61-113">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="15e61-114">驗證需要每個字串採用電話號碼的形式，其中數字的三個群組以連字號分隔、前兩個群組包含三位數，而第三個群組包含四位數。</span><span class="sxs-lookup"><span data-stu-id="15e61-114">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="15e61-115">使用 `^\\d{3}-\\d{3}-\\d{4}$` 規則運算式即可完成此作業。</span><span class="sxs-lookup"><span data-stu-id="15e61-115">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="15e61-116">如需詳細資訊，請參閱[規則運算式語言 - 快速參考](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)。</span><span class="sxs-lookup"><span data-stu-id="15e61-116">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="15e61-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="15e61-117">See Also</span></span>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [<span data-ttu-id="15e61-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="15e61-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="15e61-119">字串</span><span class="sxs-lookup"><span data-stu-id="15e61-119">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="15e61-120">.NET Framework 規則運算式</span><span class="sxs-lookup"><span data-stu-id="15e61-120">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)  
 [<span data-ttu-id="15e61-121">規則運算式語言 - 快速參考</span><span class="sxs-lookup"><span data-stu-id="15e61-121">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
