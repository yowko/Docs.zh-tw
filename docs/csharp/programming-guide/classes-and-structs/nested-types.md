---
title: 巢狀類型 - C# 程式設計手冊
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626486"
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="5b238-102">巢狀類型 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5b238-102">Nested Types (C# Programming Guide)</span></span>

<span data-ttu-id="5b238-103">在[類](../../language-reference/keywords/class.md)、[結構](../../language-reference/builtin-types/struct.md)或[介面](../../language-reference/keywords/interface.md)中定義的類型稱為巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="5b238-103">A type defined within a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) is called a nested type.</span></span> <span data-ttu-id="5b238-104">例如：</span><span class="sxs-lookup"><span data-stu-id="5b238-104">For example</span></span>

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

<span data-ttu-id="5b238-105">無論外部類型是類、介面還是結構，巢狀型別預設為[私有](../../language-reference/keywords/private.md)類型 。它們只能從包含類型訪問。</span><span class="sxs-lookup"><span data-stu-id="5b238-105">Regardless of whether the outer type is a class, interface, or struct, nested types default to [private](../../language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="5b238-106">在上述範例中，外部類型無法存取 `Nested` 類別。</span><span class="sxs-lookup"><span data-stu-id="5b238-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span>

<span data-ttu-id="5b238-107">您也可以指定[存取修飾詞](../../language-reference/keywords/access-modifiers.md)來定義巢狀型別的存取範圍，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5b238-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="5b238-108">**類別**的巢狀型別可以是 [public](../../language-reference/keywords/public.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md)、[private](../../language-reference/keywords/private.md) 或 [private protected](../../language-reference/keywords/private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="5b238-108">Nested types of a **class** can be [public](../../language-reference/keywords/public.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md), [private](../../language-reference/keywords/private.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span>

   <span data-ttu-id="5b238-109">不過，在 [sealed 類別](../../language-reference/keywords/sealed.md)內部定義 `protected`、`protected internal` 或 `private protected` 巢狀類別會產生編譯器警告 [CS0628](../../misc/cs0628.md)「在 sealed 類別中已宣告新的 protected 成員」。</span><span class="sxs-lookup"><span data-stu-id="5b238-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="5b238-110">**struct** 的巢狀型別可以是 [public](../../language-reference/keywords/public.md)、[internal](../../language-reference/keywords/internal.md) 或 [private](../../language-reference/keywords/private.md)。</span><span class="sxs-lookup"><span data-stu-id="5b238-110">Nested types of a **struct** can be [public](../../language-reference/keywords/public.md), [internal](../../language-reference/keywords/internal.md), or [private](../../language-reference/keywords/private.md).</span></span>

<span data-ttu-id="5b238-111">下列範例會將 `Nested` 類別設為 public：</span><span class="sxs-lookup"><span data-stu-id="5b238-111">The following example makes the `Nested` class public:</span></span>

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

<span data-ttu-id="5b238-112">巢狀型別或內部類型可存取包含類型或外部類型。</span><span class="sxs-lookup"><span data-stu-id="5b238-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="5b238-113">若要存取包含類型，請將它當作引數傳遞至巢狀型別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="5b238-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="5b238-114">例如：</span><span class="sxs-lookup"><span data-stu-id="5b238-114">For example:</span></span>

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

<span data-ttu-id="5b238-115">巢狀型別可以存取其包含型別可存取的所有成員。</span><span class="sxs-lookup"><span data-stu-id="5b238-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="5b238-116">它可存取包含型別的 private 和 protected 成員，包括任何繼承的 protected 成員。</span><span class="sxs-lookup"><span data-stu-id="5b238-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>

<span data-ttu-id="5b238-117">在先前的宣告，`Nested` 類別的完整名稱為 `Container.Nested`。</span><span class="sxs-lookup"><span data-stu-id="5b238-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="5b238-118">這是用來建立巢狀類別新執行個體的名稱，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5b238-118">This is the name used to create a new instance of the nested class, as follows:</span></span>

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a><span data-ttu-id="5b238-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b238-119">See also</span></span>

- [<span data-ttu-id="5b238-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5b238-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5b238-121">類別和結構</span><span class="sxs-lookup"><span data-stu-id="5b238-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="5b238-122">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="5b238-122">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="5b238-123">建構函式</span><span class="sxs-lookup"><span data-stu-id="5b238-123">Constructors</span></span>](./constructors.md)
