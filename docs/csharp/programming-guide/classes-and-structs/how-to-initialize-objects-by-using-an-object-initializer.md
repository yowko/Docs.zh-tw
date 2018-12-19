---
title: HOW TO：使用物件初始設定式初始化物件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 82efa751ad70fd2741ec2e306f56f2be06abad11
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244985"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="a6637-102">HOW TO：使用物件初始設定式初始化物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a6637-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="a6637-103">您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。</span><span class="sxs-lookup"><span data-stu-id="a6637-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="a6637-104">下列範例示範如何搭配具名物件使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="a6637-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="a6637-105">編譯器會先存取預設執行個體建構函式，再處理成員初始化，來處理物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="a6637-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="a6637-106">因此，如果預設建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。</span><span class="sxs-lookup"><span data-stu-id="a6637-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="a6637-107">如果您要定義匿名型別，則必須使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="a6637-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="a6637-108">如需詳細資訊，請參閱[＜How to：在查詢中傳回項目屬性的子集](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)。</span><span class="sxs-lookup"><span data-stu-id="a6637-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6637-109">範例</span><span class="sxs-lookup"><span data-stu-id="a6637-109">Example</span></span>  
 <span data-ttu-id="a6637-110">下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。</span><span class="sxs-lookup"><span data-stu-id="a6637-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="a6637-111">範例</span><span class="sxs-lookup"><span data-stu-id="a6637-111">Example</span></span>  
 <span data-ttu-id="a6637-112">下列範例示範如何使用集合初始設定式，來初始化 `StudentName` 類型的集合。</span><span class="sxs-lookup"><span data-stu-id="a6637-112">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="a6637-113">請注意，集合初始設定式是一系列以逗號分隔的物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="a6637-113">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a6637-114">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a6637-114">Compiling the Code</span></span>  
 <span data-ttu-id="a6637-115">若要執行此程式碼，請將該類別複製並貼到已在 Visual Studio 中建立的 Visual C# 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="a6637-115">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6637-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6637-116">See Also</span></span>

- [<span data-ttu-id="a6637-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a6637-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a6637-118">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="a6637-118">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
