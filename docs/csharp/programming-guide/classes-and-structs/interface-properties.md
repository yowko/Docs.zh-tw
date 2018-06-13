---
title: 介面屬性 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: bfa03c7ebe82f3f6a03666d908a5fa9d4e386172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325405"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="ba7f8-102">介面屬性 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="ba7f8-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="ba7f8-103">屬性可以宣告於 [interface](../../../csharp/language-reference/keywords/interface.md) 上。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="ba7f8-104">介面索引子存取子的範例如下：</span><span class="sxs-lookup"><span data-stu-id="ba7f8-104">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="ba7f8-105">介面屬性的存取子沒有主體。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="ba7f8-106">因此，存取子的目的是指出屬性是讀寫、唯讀還是唯寫。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba7f8-107">範例</span><span class="sxs-lookup"><span data-stu-id="ba7f8-107">Example</span></span>  
 <span data-ttu-id="ba7f8-108">在此範例中，`IEmployee` 介面具有讀寫屬性 `Name` 和唯讀屬性 `Counter`。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="ba7f8-109">`Employee` 類別會實作 `IEmployee` 介面，並使用這兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="ba7f8-110">程式會讀取新員工的姓名和目前員工人數，並顯示員工姓名和計算的員工人數。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="ba7f8-111">您可以使用屬性的完整名稱，而屬性參考在其中宣告成員的介面。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="ba7f8-112">例如: </span><span class="sxs-lookup"><span data-stu-id="ba7f8-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="ba7f8-113">這稱為[明確介面實作](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="ba7f8-114">例如，如果 `Employee` 類別實作 `ICitizen` 和 `IEmployee` 這兩個介面，而且這兩個介面都具有 `Name` 屬性，則需要明確介面成員實作。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="ba7f8-115">也就是說，下列屬性宣告：</span><span class="sxs-lookup"><span data-stu-id="ba7f8-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="ba7f8-116">在 `IEmployee` 介面上實作 `Name` 屬性，而下列宣告：</span><span class="sxs-lookup"><span data-stu-id="ba7f8-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="ba7f8-117">在 `ICitizen` 介面上實作 `Name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ba7f8-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="ba7f8-118">範例輸出</span><span class="sxs-lookup"><span data-stu-id="ba7f8-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="ba7f8-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba7f8-119">See Also</span></span>  
 [<span data-ttu-id="ba7f8-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ba7f8-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ba7f8-121">屬性</span><span class="sxs-lookup"><span data-stu-id="ba7f8-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="ba7f8-122">使用屬性</span><span class="sxs-lookup"><span data-stu-id="ba7f8-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="ba7f8-123">屬性與索引子之間的比較</span><span class="sxs-lookup"><span data-stu-id="ba7f8-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [<span data-ttu-id="ba7f8-124">索引子</span><span class="sxs-lookup"><span data-stu-id="ba7f8-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="ba7f8-125">介面</span><span class="sxs-lookup"><span data-stu-id="ba7f8-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
