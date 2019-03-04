---
title: HOW TO：在查詢中傳回項目屬性的子集 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 80f13250576957b252d6d83bfbcf70346b49b5a7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980716"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="d5570-102">作法：在查詢中傳回項目屬性的子集 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d5570-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="d5570-103">如果下列兩個條件都成立，請在查詢運算式中使用匿名型別：</span><span class="sxs-lookup"><span data-stu-id="d5570-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="d5570-104">您只要傳回每個來源項目的部分屬性。</span><span class="sxs-lookup"><span data-stu-id="d5570-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="d5570-105">您不需要儲存執行查詢所在之方法範圍外的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="d5570-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="d5570-106">如果您只要從每個來源項目傳回一個屬性或欄位，只要在 `select` 子句中使用點運算子即可。</span><span class="sxs-lookup"><span data-stu-id="d5570-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="d5570-107">例如，若只要傳回每個 `student` 的 `ID`，請如下所示撰寫 `select` 子句：</span><span class="sxs-lookup"><span data-stu-id="d5570-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="d5570-108">範例</span><span class="sxs-lookup"><span data-stu-id="d5570-108">Example</span></span>  
 <span data-ttu-id="d5570-109">下列範例示範如何使用匿名型別，只傳回每個來源項目中符合指定條件的屬性子集。</span><span class="sxs-lookup"><span data-stu-id="d5570-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="d5570-110">請注意，如果未指定名稱，匿名型別會針對來源項目的屬性使用其名稱。</span><span class="sxs-lookup"><span data-stu-id="d5570-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="d5570-111">若要為匿名型別中的屬性指定新名稱，請如下所示撰寫 `select` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d5570-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="d5570-112">如果您在上述範例中嘗試這樣做，則必須同時變更 `Console.WriteLine` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d5570-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d5570-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d5570-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d5570-114">若要執行此程式碼，請將該類別複製並貼到已在 Visual Studio 中建立的 Visual C# 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="d5570-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="d5570-115">根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，而且會有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="d5570-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="d5570-116">如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。</span><span class="sxs-lookup"><span data-stu-id="d5570-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="d5570-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5570-117">See also</span></span>

- [<span data-ttu-id="d5570-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d5570-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d5570-119">匿名類型</span><span class="sxs-lookup"><span data-stu-id="d5570-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="d5570-120">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="d5570-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
