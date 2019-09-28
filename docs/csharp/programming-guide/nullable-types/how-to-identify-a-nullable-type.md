---
title: 如何：識別可為 null 的實值C#類型-程式設計指南
ms.custom: seodec18
description: 瞭解如何判斷類型是否為可為 null 的實數值型別，或實例是否屬於可為 null 的實數值型別
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 15b1ffedf57648955ee5a004514841a5d140292b
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392603"
---
# <a name="how-to-identify-a-nullable-value-type-c-programming-guide"></a><span data-ttu-id="bbc23-103">如何：識別可為 null 的實值C#型別（程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="bbc23-103">How to: identify a nullable value type (C# Programming Guide)</span></span>

<span data-ttu-id="bbc23-104">下列範例示範如何判斷 <xref:System.Type?displayProperty=nameWithType> 實例是否代表封閉式泛型可為 null 的實值型別，也就是具有指定之型別參數的 <xref:System.Nullable%601?displayProperty=nameWithType> 型別 `T`：</span><span class="sxs-lookup"><span data-stu-id="bbc23-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a closed generic nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="bbc23-105">如範例所示，您使用 [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) 運算子來建立 <xref:System.Type?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="bbc23-105">As the example shows, you use the [typeof](../../language-reference/operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>

<span data-ttu-id="bbc23-106">如果您想要判斷實例是否屬於可為 null 的實值型別，請不要使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法來取得要使用上述程式碼測試的 <xref:System.Type> 實例。</span><span class="sxs-lookup"><span data-stu-id="bbc23-106">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="bbc23-107">當您在可為 null 的實數值型別的實例上呼叫 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法時，實例會被[封裝](using-nullable-types.md#boxing-and-unboxing)為 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="bbc23-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="bbc23-108">當可為 null 的實數值型別之非 null 實例的裝箱相當於基礎類型值的裝箱時，<xref:System.Object.GetType%2A> 會傳回代表可為 null 實數值型別之基礎類型的 @no__t 1 物件：</span><span class="sxs-lookup"><span data-stu-id="bbc23-108">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="bbc23-109">請勿使用[is](../../language-reference/keywords/is.md)運算子來判斷實例是否屬於可為 null 的實數值型別。</span><span class="sxs-lookup"><span data-stu-id="bbc23-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="bbc23-110">如下列範例所示，您無法使用 `is` 運算子來區別可為 null 的實數值型別和其基礎類型的實例類型：</span><span class="sxs-lookup"><span data-stu-id="bbc23-110">As the following example shows, you cannot distinguish types of instances of a nullable value type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="bbc23-111">您可以使用下列範例所顯示的程式碼，來判斷實例是否為可為 null 的實數值型別：</span><span class="sxs-lookup"><span data-stu-id="bbc23-111">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]

## <a name="see-also"></a><span data-ttu-id="bbc23-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbc23-112">See also</span></span>

- [<span data-ttu-id="bbc23-113">可為 Null 的實值型別</span><span class="sxs-lookup"><span data-stu-id="bbc23-113">Nullable value types</span></span>](index.md)
- [<span data-ttu-id="bbc23-114">使用可為 null 的實數值型別</span><span class="sxs-lookup"><span data-stu-id="bbc23-114">Using nullable value types</span></span>](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
