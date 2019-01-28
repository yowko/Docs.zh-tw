---
title: 私用建構函式 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: e406b72e5d2932464c407dce014dd8eceee59fb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577291"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="66527-102">私用建構函式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="66527-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="66527-103">私用建構函式是一種特殊的執行個體建構函式。</span><span class="sxs-lookup"><span data-stu-id="66527-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="66527-104">它通常會用於只包含靜態成員的類別。</span><span class="sxs-lookup"><span data-stu-id="66527-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="66527-105">如果類別具有一或多個私用建構函式，而且沒有任何公用建構函式，則其他類別 (巢狀類別除外) 無法建立此類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="66527-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="66527-106">例如：</span><span class="sxs-lookup"><span data-stu-id="66527-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 <span data-ttu-id="66527-107">宣告空的建構函式可防止自動產生預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="66527-107">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="66527-108">請注意，如果您未搭配建構函式使用存取修飾詞，預設仍會是私用的。</span><span class="sxs-lookup"><span data-stu-id="66527-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="66527-109">不過，通常會明確使用 [private](../../../csharp/language-reference/keywords/private.md) 修飾詞來指出無法具現化類別。</span><span class="sxs-lookup"><span data-stu-id="66527-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="66527-110">當類別沒有執行個體欄位或方法 (例如 <xref:System.Math> 類別)，或是您要呼叫方法以取得類別的執行個體時，可以使用私用建構函式來防止建立類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="66527-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="66527-111">如果類別中的所有方法都是靜態的，請考慮將整個類別變為靜態。</span><span class="sxs-lookup"><span data-stu-id="66527-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="66527-112">如需詳細資訊，請參閱[靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="66527-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="66527-113">範例</span><span class="sxs-lookup"><span data-stu-id="66527-113">Example</span></span>  
 <span data-ttu-id="66527-114">以下是使用私用建構函式的類別範例。</span><span class="sxs-lookup"><span data-stu-id="66527-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 <span data-ttu-id="66527-115">請注意，如果您將範例中的下列陳述式取消註解，這時將會產生錯誤，因為建構函式會因其保護層級而無法存取：</span><span class="sxs-lookup"><span data-stu-id="66527-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="66527-116">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="66527-116">C# Language Specification</span></span>  

<span data-ttu-id="66527-117">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)的[私用建構式](~/_csharplang/spec/classes.md#private-constructors)。</span><span class="sxs-lookup"><span data-stu-id="66527-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="66527-118">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="66527-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="66527-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66527-119">See also</span></span>

- [<span data-ttu-id="66527-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="66527-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="66527-121">類別和結構</span><span class="sxs-lookup"><span data-stu-id="66527-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="66527-122">建構函式</span><span class="sxs-lookup"><span data-stu-id="66527-122">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="66527-123">完成項</span><span class="sxs-lookup"><span data-stu-id="66527-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="66527-124">private</span><span class="sxs-lookup"><span data-stu-id="66527-124">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="66527-125">public</span><span class="sxs-lookup"><span data-stu-id="66527-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)
