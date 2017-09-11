---
title: "如何：在查詢中傳回項目屬性的子集 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: de6f4f1aeb07d7878d02b4f51e6f42b69d0bdcf5
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="42c0e-102">如何：在查詢中傳回項目屬性的子集 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="42c0e-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="42c0e-103">如果下列兩個條件都成立，請在查詢運算式中使用匿名型別：</span><span class="sxs-lookup"><span data-stu-id="42c0e-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="42c0e-104">您只要傳回每個來源項目的部分屬性。</span><span class="sxs-lookup"><span data-stu-id="42c0e-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="42c0e-105">您不需要儲存執行查詢所在之方法範圍外的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="42c0e-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="42c0e-106">如果您只要從每個來源項目傳回一個屬性或欄位，只要在 `select` 子句中使用點運算子即可。</span><span class="sxs-lookup"><span data-stu-id="42c0e-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="42c0e-107">例如，若只要傳回每個 `student` 的 `ID`，請如下所示撰寫 `select` 子句：</span><span class="sxs-lookup"><span data-stu-id="42c0e-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="42c0e-108">範例</span><span class="sxs-lookup"><span data-stu-id="42c0e-108">Example</span></span>  
 <span data-ttu-id="42c0e-109">下列範例示範如何使用匿名型別，只傳回每個來源項目中符合指定條件的屬性子集。</span><span class="sxs-lookup"><span data-stu-id="42c0e-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 <span data-ttu-id="42c0e-110">[!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="42c0e-110">[!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]</span></span>  
  
 <span data-ttu-id="42c0e-111">請注意，如果未指定名稱，匿名型別會針對來源項目的屬性使用其名稱。</span><span class="sxs-lookup"><span data-stu-id="42c0e-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="42c0e-112">若要為匿名型別中的屬性指定新名稱，請如下所示撰寫 `select` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="42c0e-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="42c0e-113">如果您在上述範例中嘗試這樣做，則必須同時變更 `Console.WriteLine` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="42c0e-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="42c0e-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="42c0e-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="42c0e-115">若要執行此程式碼，請將該類別複製並貼到 [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] 中所建立的 Visual C# 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="42c0e-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="42c0e-116">根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，而且會有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="42c0e-116">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="42c0e-117">如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。</span><span class="sxs-lookup"><span data-stu-id="42c0e-117">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="42c0e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42c0e-118">See Also</span></span>  
 <span data-ttu-id="42c0e-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="42c0e-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="42c0e-120">[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="42c0e-120">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 [<span data-ttu-id="42c0e-121">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="42c0e-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

