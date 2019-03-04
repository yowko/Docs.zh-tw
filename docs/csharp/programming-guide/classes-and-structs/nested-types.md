---
title: 巢狀類型 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 7269f925b3fc78eea04249984697899b1997c3fb
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976703"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="f3566-102">巢狀類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f3566-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="f3566-103">在 [class](../../../csharp/language-reference/keywords/class.md) 或 [struct](../../../csharp/language-reference/keywords/struct.md) 內定義的類型稱為巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="f3566-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="f3566-104">例如：</span><span class="sxs-lookup"><span data-stu-id="f3566-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
<span data-ttu-id="f3566-105">不論外部類型是 class 或 struct，巢狀型別都預設為 [private](../../../csharp/language-reference/keywords/private.md)；它們只能從其包含類型中進行存取。</span><span class="sxs-lookup"><span data-stu-id="f3566-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="f3566-106">在上述範例中，外部類型無法存取 `Nested` 類別。</span><span class="sxs-lookup"><span data-stu-id="f3566-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="f3566-107">您也可以指定[存取修飾詞](../../language-reference/keywords/access-modifiers.md)來定義巢狀型別的存取範圍，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3566-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="f3566-108">**類別**的巢狀型別可以是 [public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)、[private](../../../csharp/language-reference/keywords/private.md) 或 [private protected](../../../csharp/language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="f3566-108">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="f3566-109">不過，在 [sealed 類別](../../language-reference/keywords/sealed.md)內部定義 `protected`、`protected internal` 或 `private protected` 巢狀類別會產生編譯器警告 [CS0628](../../misc/cs0628.md)「在 sealed 類別中已宣告新的 protected 成員」。</span><span class="sxs-lookup"><span data-stu-id="f3566-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="f3566-110">**struct** 的巢狀型別可以是 [public](../../../csharp/language-reference/keywords/public.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 [private](../../../csharp/language-reference/keywords/private.md)。</span><span class="sxs-lookup"><span data-stu-id="f3566-110">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="f3566-111">下列範例會將 `Nested` 類別設為 public：</span><span class="sxs-lookup"><span data-stu-id="f3566-111">The following example makes the `Nested` class public:</span></span>
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 <span data-ttu-id="f3566-112">巢狀型別或內部類型可存取包含類型或外部類型。</span><span class="sxs-lookup"><span data-stu-id="f3566-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="f3566-113">若要存取包含類型，請將它當作引數傳遞至巢狀型別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="f3566-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="f3566-114">例如：</span><span class="sxs-lookup"><span data-stu-id="f3566-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 <span data-ttu-id="f3566-115">巢狀型別可以存取其包含型別可存取的所有成員。</span><span class="sxs-lookup"><span data-stu-id="f3566-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="f3566-116">它可存取包含型別的 private 和 protected 成員，包括任何繼承的 protected 成員。</span><span class="sxs-lookup"><span data-stu-id="f3566-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="f3566-117">在先前的宣告，`Nested` 類別的完整名稱為 `Container.Nested`。</span><span class="sxs-lookup"><span data-stu-id="f3566-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="f3566-118">這是用來建立巢狀類別新執行個體的名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f3566-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a><span data-ttu-id="f3566-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3566-119">See also</span></span>

- [<span data-ttu-id="f3566-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f3566-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f3566-121">類別和結構</span><span class="sxs-lookup"><span data-stu-id="f3566-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="f3566-122">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="f3566-122">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="f3566-123">建構函式</span><span class="sxs-lookup"><span data-stu-id="f3566-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
