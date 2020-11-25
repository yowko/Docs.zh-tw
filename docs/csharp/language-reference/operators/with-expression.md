---
title: 'with expression-c # 參考'
description: '瞭解執行 c # 記錄之非破壞性變化的 with 運算式'
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: d7d3758c8c5da7859974b5b50b63d2a5ca16b24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702221"
---
# <a name="with-expression-c-reference"></a><span data-ttu-id="86247-103">with expression (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="86247-103">with expression (C# reference)</span></span>

<span data-ttu-id="86247-104">在 c # 9.0 和更新版本中提供， `with` 運算式會產生其 [記錄](../../whats-new/csharp-9.md#record-types) 運算元的複本，並已修改指定的屬性和欄位：</span><span class="sxs-lookup"><span data-stu-id="86247-104">Available in C# 9.0 and later, a `with` expression produces a copy of its [record](../../whats-new/csharp-9.md#record-types) operand with the specified properties and fields modified:</span></span>

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

<span data-ttu-id="86247-105">如先前的範例所示，您可以使用 [物件初始化運算式](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) 語法來指定要修改的成員及其新值。</span><span class="sxs-lookup"><span data-stu-id="86247-105">As the preceding example shows, you use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify what members to modify and their new values.</span></span> <span data-ttu-id="86247-106">在 `with` 運算式中，左邊運算元必須是記錄類型。</span><span class="sxs-lookup"><span data-stu-id="86247-106">In a `with` expression, a left-hand operand must be of a record type.</span></span>

<span data-ttu-id="86247-107">運算式的結果與 `with` 運算式的運算元具有相同的執行時間類型，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="86247-107">The result of a `with` expression has the same runtime type as the expression's operand, as the following example shows:</span></span>

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

<span data-ttu-id="86247-108">在參考型別成員的案例中，複製記錄時，只會複製實例的參考。</span><span class="sxs-lookup"><span data-stu-id="86247-108">In the case of a reference-type member, only the reference to an instance is copied when a record is copied.</span></span> <span data-ttu-id="86247-109">複製和原始記錄都可以存取相同的參考型別實例。</span><span class="sxs-lookup"><span data-stu-id="86247-109">Both the copy and original record have access to the same reference-type instance.</span></span> <span data-ttu-id="86247-110">下列範例示範了該行為：</span><span class="sxs-lookup"><span data-stu-id="86247-110">The following example demonstrates that behavior:</span></span>

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

<span data-ttu-id="86247-111">任何記錄類型都有 *複製* 的函式。</span><span class="sxs-lookup"><span data-stu-id="86247-111">Any record type has the *copy constructor*.</span></span> <span data-ttu-id="86247-112">這是具有包含記錄類型之單一參數的函式。</span><span class="sxs-lookup"><span data-stu-id="86247-112">That is a constructor with a single parameter of the containing record type.</span></span> <span data-ttu-id="86247-113">它會將其引數的狀態複製到新的記錄實例。</span><span class="sxs-lookup"><span data-stu-id="86247-113">It copies the state of its argument to a new record instance.</span></span> <span data-ttu-id="86247-114">在評估運算式時 `with` ，會呼叫複製函式以根據原始記錄具現化新的記錄實例。</span><span class="sxs-lookup"><span data-stu-id="86247-114">At evaluation of a `with` expression, the copy constructor gets called to instantiate a new record instance based on an original record.</span></span> <span data-ttu-id="86247-115">之後，會根據指定的修改更新新的實例。</span><span class="sxs-lookup"><span data-stu-id="86247-115">After that, the new instance gets updated according to the specified modifications.</span></span> <span data-ttu-id="86247-116">根據預設，複製的函式是隱含的，也就是編譯器產生的。</span><span class="sxs-lookup"><span data-stu-id="86247-116">By default, the copy constructor is implicit, that is, compiler-generated.</span></span> <span data-ttu-id="86247-117">如果您需要自訂記錄複製語義，請使用所需的行為明確宣告複製的函式。</span><span class="sxs-lookup"><span data-stu-id="86247-117">If you need to customize the record copy semantics, explicitly declare a copy constructor with the desired behavior.</span></span> <span data-ttu-id="86247-118">下列範例會使用明確的複製函式來更新上述範例。</span><span class="sxs-lookup"><span data-stu-id="86247-118">The following example updates the preceding example with an explicit copy constructor.</span></span> <span data-ttu-id="86247-119">複製記錄時，新的複製行為是複製清單專案，而不是清單參考：</span><span class="sxs-lookup"><span data-stu-id="86247-119">The new copy behavior is to copy list items instead of a list reference when a record is copied:</span></span>

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a><span data-ttu-id="86247-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="86247-120">C# language specification</span></span>

<span data-ttu-id="86247-121">如需詳細資訊，請參閱下列 [記錄功能的建議事項附注](~/_csharplang/proposals/csharp-9.0/records.md)：</span><span class="sxs-lookup"><span data-stu-id="86247-121">For more information, see the following sections of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md):</span></span>

- [<span data-ttu-id="86247-122">`with` 表達</span><span class="sxs-lookup"><span data-stu-id="86247-122">`with` expression</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [<span data-ttu-id="86247-123">複製和複製成員</span><span class="sxs-lookup"><span data-stu-id="86247-123">Copy and Clone members</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a><span data-ttu-id="86247-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86247-124">See also</span></span>

- [<span data-ttu-id="86247-125">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="86247-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="86247-126">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="86247-126">C# operators and expressions</span></span>](index.md)
