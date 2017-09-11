---
title: "私用建構函式 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
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
ms.openlocfilehash: 1ccd3db5f95e3a237bb37d9e09c34f415fcfd752
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="73de8-102">私用建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="73de8-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="73de8-103">私用建構函式是一種特殊的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="73de8-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="73de8-104">它通常會用於只包含靜態成員的類別。</span><span class="sxs-lookup"><span data-stu-id="73de8-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="73de8-105">如果類別具有一或多個私用建構函式，而且沒有任何公用建構函式，則其他類別 (巢狀類別除外) 無法建立此類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="73de8-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="73de8-106">例如: </span><span class="sxs-lookup"><span data-stu-id="73de8-106">For example:</span></span>  
  
 <span data-ttu-id="73de8-107">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="73de8-107">[!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]</span></span>  
  
 <span data-ttu-id="73de8-108">宣告空的建構函式可防止自動產生預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="73de8-108">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="73de8-109">請注意，如果您未搭配建構函式使用存取修飾詞，預設仍會是私用的。</span><span class="sxs-lookup"><span data-stu-id="73de8-109">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="73de8-110">不過，通常會明確使用 [private](../../../csharp/language-reference/keywords/private.md) 修飾詞來指出無法具現化類別。</span><span class="sxs-lookup"><span data-stu-id="73de8-110">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="73de8-111">當類別沒有執行個體欄位或方法 (例如 <xref:System.Math> 類別)，或是您要呼叫方法以取得類別的執行個體時，可以使用私用建構函式來防止建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="73de8-111">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="73de8-112">如果類別中的所有方法都是靜態的，請考慮將整個類別變為靜態。</span><span class="sxs-lookup"><span data-stu-id="73de8-112">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="73de8-113">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="73de8-113">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73de8-114">範例</span><span class="sxs-lookup"><span data-stu-id="73de8-114">Example</span></span>  
 <span data-ttu-id="73de8-115">以下是使用私用建構函式的類別範例。</span><span class="sxs-lookup"><span data-stu-id="73de8-115">The following is an example of a class using a private constructor.</span></span>  
  
 <span data-ttu-id="73de8-116">[!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="73de8-116">[!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]</span></span>  
  
 <span data-ttu-id="73de8-117">請注意，如果您將範例中的下列陳述式取消註解，這時將會產生錯誤，因為建構函式會因其保護層級而無法存取：</span><span class="sxs-lookup"><span data-stu-id="73de8-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 <span data-ttu-id="73de8-118">[!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="73de8-118">[!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="73de8-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="73de8-119">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73de8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73de8-120">See Also</span></span>  
 <span data-ttu-id="73de8-121">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="73de8-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="73de8-122">[類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="73de8-122">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="73de8-123">[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="73de8-123">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="73de8-124">[完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="73de8-124">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 <span data-ttu-id="73de8-125">[private](../../../csharp/language-reference/keywords/private.md) </span><span class="sxs-lookup"><span data-stu-id="73de8-125">[private](../../../csharp/language-reference/keywords/private.md) </span></span>  
 [<span data-ttu-id="73de8-126">public</span><span class="sxs-lookup"><span data-stu-id="73de8-126">public</span></span>](../../../csharp/language-reference/keywords/public.md)

