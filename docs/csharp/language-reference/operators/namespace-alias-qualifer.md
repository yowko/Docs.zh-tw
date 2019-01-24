---
title: ':: 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ::_CSharpKeyword
helpviewer_keywords:
- ':: operator [C#]'
- 'namespaces [C#], :: operator'
- namespace alias qualifier operator (::) [C#]
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
ms.openlocfilehash: 2618131f27271e7c06cb6d425fc22b5bd9750c49
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333313"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="47f7e-102">:: 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="47f7e-102">:: operator (C# Reference)</span></span>

<span data-ttu-id="47f7e-103">命名空間別名限定詞 (`::`) 用來查閱識別碼。</span><span class="sxs-lookup"><span data-stu-id="47f7e-103">The namespace alias qualifier (`::`) is used to look up identifiers.</span></span> <span data-ttu-id="47f7e-104">它一律位在兩個識別碼之間，如下例所示︰</span><span class="sxs-lookup"><span data-stu-id="47f7e-104">It is always positioned between two identifiers, as in this example:</span></span>

[!code-csharp[csRefOperators#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#27)]

<span data-ttu-id="47f7e-105">`::` 運算子也可以搭配「using alias 指示詞」使用：</span><span class="sxs-lookup"><span data-stu-id="47f7e-105">The `::` operator can also be used with a *using alias directive*:</span></span>

```csharp
// using Col=System.Collections.Generic;
var numbers = new Col::List<int> { 1, 2, 3 };
```

## <a name="remarks"></a><span data-ttu-id="47f7e-106">備註</span><span class="sxs-lookup"><span data-stu-id="47f7e-106">Remarks</span></span>

<span data-ttu-id="47f7e-107">命名空間別名限定詞可以是 `global`。</span><span class="sxs-lookup"><span data-stu-id="47f7e-107">The namespace alias qualifier can be `global`.</span></span> <span data-ttu-id="47f7e-108">這會在全域命名空間中叫用查詢，不是在別名命名空間中。</span><span class="sxs-lookup"><span data-stu-id="47f7e-108">This invokes a lookup in the global namespace, rather than an aliased namespace.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="47f7e-109">如需詳細資訊</span><span class="sxs-lookup"><span data-stu-id="47f7e-109">For more information</span></span>

<span data-ttu-id="47f7e-110">如需如何使用 `::` 運算子的範例，請參閱下一節︰</span><span class="sxs-lookup"><span data-stu-id="47f7e-110">For an example of how to use the `::` operator, see the following section:</span></span>

- [<span data-ttu-id="47f7e-111">如何：使用全域命名空間別名</span><span class="sxs-lookup"><span data-stu-id="47f7e-111">How to: Use the Global Namespace Alias</span></span>](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)

## <a name="c-language-specification"></a><span data-ttu-id="47f7e-112">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="47f7e-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="47f7e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47f7e-113">See also</span></span>

- [<span data-ttu-id="47f7e-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="47f7e-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47f7e-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="47f7e-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47f7e-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="47f7e-116">C# operators</span></span>](index.md)
- [<span data-ttu-id="47f7e-117">命名空間關鍵字</span><span class="sxs-lookup"><span data-stu-id="47f7e-117">Namespace Keywords</span></span>](../keywords/namespace-keywords.md)
- [<span data-ttu-id="47f7e-118">. 運算子</span><span class="sxs-lookup"><span data-stu-id="47f7e-118">. operator</span></span>](member-access-operator.md)
- [<span data-ttu-id="47f7e-119">外部別名</span><span class="sxs-lookup"><span data-stu-id="47f7e-119">extern alias</span></span>](../keywords/extern-alias.md)