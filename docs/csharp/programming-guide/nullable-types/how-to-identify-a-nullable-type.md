---
title: 如何：識別可為 Null 的型別 (C# 程式設計手冊)
description: 了解如何判斷某個類型或執行個體是否屬於可為 Null 的型別
ms.date: 08/06/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: c65f80974154d81b5ddf239b617eeeda68434e09
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178241"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="87174-103">如何：識別可為 Null 的型別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="87174-103">How to: Identify a nullable type (C# Programming Guide)</span></span>

<span data-ttu-id="87174-104">下列範例示範如何判斷 <xref:System.Type?displayProperty=nameWithType> 執行個體是否代表可為 Null 的型別：</span><span class="sxs-lookup"><span data-stu-id="87174-104">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a nullable type:</span></span>

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

<span data-ttu-id="87174-105">如範例所示，您使用 [typeof](../../language-reference/keywords/typeof.md) 運算子來建立 <xref:System.Type?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="87174-105">As the example shows, you use the [typeof](../../language-reference/keywords/typeof.md) operator to create a <xref:System.Type?displayProperty=nameWithType> object.</span></span>  
  
<span data-ttu-id="87174-106">如果您想要判斷某個執行個體是否屬於可為 Null 的型別，請勿使用 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法透過上述程式碼來測試 <xref:System.Type> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="87174-106">If you want to determine whether an instance is of a nullable type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="87174-107">當您在可為 Null 的型別執行個體上呼叫 <xref:System.Object.GetType%2A?displayProperty=nameWithType> 方法時，該執行個體會 [Boxing](using-nullable-types.md#boxing-and-unboxing) 處理為 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="87174-107">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable type, the instance is [boxed](using-nullable-types.md#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="87174-108">由於對可為 Null 型別的非 Null 執行個體進行 Boxing 處理相當於對基礎類型的值進行 Boxing 處理，因此 <xref:System.Object.GetType%2A> 會傳回<xref:System.Type> 物件，代表可為 Null 型別的基礎型別：</span><span class="sxs-lookup"><span data-stu-id="87174-108">As boxing of a non-null instance of a nullable type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> object that represents the underlying type of a nullable type:</span></span>

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

<span data-ttu-id="87174-109">請勿使用 [is](../../language-reference/keywords/is.md) 運算子來判斷某個執行個體是否屬於可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="87174-109">Don't use the [is](../../language-reference/keywords/is.md) operator to determine whether an instance is of a nullable type.</span></span> <span data-ttu-id="87174-110">如下列範例所示，您無法使用 `is` 運算子來區別可為 Null 型別及其基礎類型的執行個體類型：</span><span class="sxs-lookup"><span data-stu-id="87174-110">As the following example shows, you cannot distinguish types of instances of a nullable type and its underlying type with using the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

<span data-ttu-id="87174-111">您可以使用下列範例所示的程式碼來判斷某個執行個體是否屬於可為 Null 的型別：</span><span class="sxs-lookup"><span data-stu-id="87174-111">You can use the code presented in the following example to determine whether an instance is of a nullable type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a><span data-ttu-id="87174-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="87174-112">See Also</span></span>

- [<span data-ttu-id="87174-113">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="87174-113">Nullable types</span></span>](index.md)  
- [<span data-ttu-id="87174-114">使用可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="87174-114">Using nullable types</span></span>](using-nullable-types.md)  
- <xref:System.Nullable.GetUnderlyingType%2A>  
