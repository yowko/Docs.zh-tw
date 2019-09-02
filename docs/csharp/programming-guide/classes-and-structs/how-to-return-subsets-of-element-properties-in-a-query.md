---
title: 作法：在查詢中傳回項目屬性的子集 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205441"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="5dcb6-102">作法：在查詢中傳回項目屬性的子集 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5dcb6-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="5dcb6-103">如果下列兩個條件都成立，請在查詢運算式中使用匿名型別：</span><span class="sxs-lookup"><span data-stu-id="5dcb6-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="5dcb6-104">您只要傳回每個來源項目的部分屬性。</span><span class="sxs-lookup"><span data-stu-id="5dcb6-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="5dcb6-105">您不需要儲存執行查詢所在之方法範圍外的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="5dcb6-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="5dcb6-106">如果您只要從每個來源項目傳回一個屬性或欄位，只要在 `select` 子句中使用點運算子即可。</span><span class="sxs-lookup"><span data-stu-id="5dcb6-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="5dcb6-107">例如，若只要傳回每個 `student` 的 `ID`，請如下所示撰寫 `select` 子句：</span><span class="sxs-lookup"><span data-stu-id="5dcb6-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="5dcb6-108">範例</span><span class="sxs-lookup"><span data-stu-id="5dcb6-108">Example</span></span>  
 <span data-ttu-id="5dcb6-109">下列範例示範如何使用匿名型別，只傳回每個來源項目中符合指定條件的屬性子集。</span><span class="sxs-lookup"><span data-stu-id="5dcb6-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="5dcb6-110">請注意，如果未指定名稱，匿名型別會針對來源項目的屬性使用其名稱。</span><span class="sxs-lookup"><span data-stu-id="5dcb6-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="5dcb6-111">若要為匿名型別中的屬性指定新名稱，請如下所示撰寫 `select` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="5dcb6-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="5dcb6-112">如果您在上述範例中嘗試這樣做，則必須同時變更 `Console.WriteLine` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="5dcb6-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5dcb6-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="5dcb6-113">Compiling the Code</span></span>  
  
<span data-ttu-id="5dcb6-114">若要執行此程式碼，請將該類別複製貼入 System.Linq 指示詞為 `using` 的 C# 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="5dcb6-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5dcb6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dcb6-115">See also</span></span>

- [<span data-ttu-id="5dcb6-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5dcb6-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5dcb6-117">匿名類型</span><span class="sxs-lookup"><span data-stu-id="5dcb6-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="5dcb6-118">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="5dcb6-118">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
