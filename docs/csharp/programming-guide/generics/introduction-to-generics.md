---
title: "泛型簡介 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: 32
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f3092eb1e5435bbced565b02d989a57abf2d52e0
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="306e2-102">泛型簡介 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="306e2-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="306e2-103">泛型類別和方法將再使用性、型別安全和效率三者結合在一起，發揮了非泛型類別和方法所無法提供的功能。</span><span class="sxs-lookup"><span data-stu-id="306e2-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="306e2-104">泛型最常搭配在其上操作的集合和方法使用。</span><span class="sxs-lookup"><span data-stu-id="306e2-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="306e2-105">.NET Framework 2.0 版類別庫提供了新的命名空間 <xref:System.Collections.Generic>，其中包含數個新的泛型集合類別。</span><span class="sxs-lookup"><span data-stu-id="306e2-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="306e2-106">建議以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 2.0 和更新版本為目標的所有應用程式使用新的泛型集合類別，而不是舊版的非泛型集合類別，例如 <xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="306e2-106">It is recommended that all applications that target the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="306e2-107">如需詳細資訊，請參閱 [.NET Framework 類別庫](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)。</span><span class="sxs-lookup"><span data-stu-id="306e2-107">For more information, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="306e2-108">當然，您也可以建立自訂的泛型型別和方法，自行處理泛型化的問題，並設計型別安全且有效率的模式。</span><span class="sxs-lookup"><span data-stu-id="306e2-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="306e2-109">下列程式碼範例顯示一個簡單的泛型連結清單類別，以供示範之用</span><span class="sxs-lookup"><span data-stu-id="306e2-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="306e2-110">(在大部分情況下，您應該使用 .NET Framework 類別庫提供的 <xref:System.Collections.Generic.List%601> 類別，而不要自行建立類別)。在幾個位置會使用型別參數 `T`，這些位置一般會使用具象類型來表示清單中儲存的項目類型。</span><span class="sxs-lookup"><span data-stu-id="306e2-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="306e2-111">這個參數可以用於下列方面：</span><span class="sxs-lookup"><span data-stu-id="306e2-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="306e2-112">作為 `AddHead` 方法中的方法參數類型。</span><span class="sxs-lookup"><span data-stu-id="306e2-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="306e2-113">作為公用方法 `GetNext` 的傳回型別，以及巢狀 `Node` 類別中的 `Data` 屬性。</span><span class="sxs-lookup"><span data-stu-id="306e2-113">As the return type of the public method `GetNext` and the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="306e2-114">作為巢狀類別中的私用成員資料類型。</span><span class="sxs-lookup"><span data-stu-id="306e2-114">As the type of the private member data in the nested class.</span></span>  
  
 <span data-ttu-id="306e2-115">請注意，T 可用於巢狀 `Node` 類別。</span><span class="sxs-lookup"><span data-stu-id="306e2-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="306e2-116">當 `GenericList<T>` 以具象類型具現化時 (例如具現化為 `GenericList<int>`)，所出現的每個 `T` 都會以 `int` 取代。</span><span class="sxs-lookup"><span data-stu-id="306e2-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 <span data-ttu-id="306e2-117">[!code-cs[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="306e2-117">[!code-cs[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]</span></span>  
  
 <span data-ttu-id="306e2-118">下列程式碼範例示範用戶端程式碼如何使用泛型 `GenericList<T>` 類別建立整數清單。</span><span class="sxs-lookup"><span data-stu-id="306e2-118">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="306e2-119">您只要變更型別引數，就能輕鬆修改下列的程式碼來建立字串清單或任何其他自訂類型的清單：</span><span class="sxs-lookup"><span data-stu-id="306e2-119">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 <span data-ttu-id="306e2-120">[!code-cs[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="306e2-120">[!code-cs[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306e2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="306e2-121">See Also</span></span>  
 <span data-ttu-id="306e2-122"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="306e2-122"><xref:System.Collections.Generic></span></span>   
<span data-ttu-id="306e2-123"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="306e2-123"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="306e2-124"> [泛型](../../../csharp/programming-guide/generics/index.md)</span><span class="sxs-lookup"><span data-stu-id="306e2-124"> [Generics](../../../csharp/programming-guide/generics/index.md)</span></span>
