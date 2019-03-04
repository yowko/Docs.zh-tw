---
title: . 運算子 - C# 參考
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836457"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4e56f-103">.</span><span class="sxs-lookup"><span data-stu-id="4e56f-103">.</span></span> <span data-ttu-id="4e56f-104">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4e56f-104">operator (C# Reference)</span></span>

<span data-ttu-id="4e56f-105">點 (`.`) 通常是用於成員存取。</span><span class="sxs-lookup"><span data-stu-id="4e56f-105">The dot, `.`, is typically used for member access.</span></span>

<span data-ttu-id="4e56f-106">您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4e56f-106">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="4e56f-107">使用 `.` 來存取命名空間內的巢狀命名空間，如下列 [`using` 指示詞](../keywords/using-directive.md)的範例所示：</span><span class="sxs-lookup"><span data-stu-id="4e56f-107">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- <span data-ttu-id="4e56f-108">使用 `.` 來形成「限定名稱」以存取命名空間內的類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="4e56f-108">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  <span data-ttu-id="4e56f-109">使用 [`using` 指示詞](../keywords/using-directive.md)來使限定名稱的使用為選擇性。</span><span class="sxs-lookup"><span data-stu-id="4e56f-109">Use the [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="4e56f-110">使用 `.` 來存取[類型成員](../../programming-guide/classes-and-structs/index.md#members) (靜態及非靜態)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="4e56f-110">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

<span data-ttu-id="4e56f-111">您也可以使用 `.` 來叫用[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="4e56f-111">You can also use `.` to invoke an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4e56f-112">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="4e56f-112">Operator overloadability</span></span>

<span data-ttu-id="4e56f-113">無法多載 `.` 運算子。</span><span class="sxs-lookup"><span data-stu-id="4e56f-113">The operator `.` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4e56f-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4e56f-114">C# language specification</span></span>

<span data-ttu-id="4e56f-115">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[成員存取](~/_csharplang/spec/expressions.md#member-access)一節。</span><span class="sxs-lookup"><span data-stu-id="4e56f-115">For more information, see the [Member access](~/_csharplang/spec/expressions.md#member-access) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e56f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e56f-116">See also</span></span>

- [<span data-ttu-id="4e56f-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4e56f-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e56f-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4e56f-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e56f-119">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="4e56f-119">C# Operators</span></span>](index.md)
- <span data-ttu-id="4e56f-120">[?. 和 ?[] 運算子](null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="4e56f-120">[?. and ?[] operators](null-conditional-operators.md)</span></span>