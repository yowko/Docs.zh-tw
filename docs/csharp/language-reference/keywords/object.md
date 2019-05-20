---
title: object - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 99ce5300d06c500d2e45897a6bd57153dc40d34e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633377"
---
# <a name="object-c-reference"></a><span data-ttu-id="1c303-102">object (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="1c303-102">object (C# Reference)</span></span>

<span data-ttu-id="1c303-103">`object` 類型是 <xref:System.Object> 在 .NET 中的別名。</span><span class="sxs-lookup"><span data-stu-id="1c303-103">The `object` type is an alias for <xref:System.Object> in .NET.</span></span> <span data-ttu-id="1c303-104">在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="1c303-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="1c303-105">您可以將任何型別的值指派給 `object` 型別的變數。</span><span class="sxs-lookup"><span data-stu-id="1c303-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="1c303-106">當實值型別的變數轉換成物件時，即稱之為 *Boxed*。</span><span class="sxs-lookup"><span data-stu-id="1c303-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="1c303-107">當型別物件的變數轉換成實值型別時，即稱之為 *Unboxed*。</span><span class="sxs-lookup"><span data-stu-id="1c303-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="1c303-108">如需詳細資訊，請參閱 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)。</span><span class="sxs-lookup"><span data-stu-id="1c303-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="example"></a><span data-ttu-id="1c303-109">範例</span><span class="sxs-lookup"><span data-stu-id="1c303-109">Example</span></span>

<span data-ttu-id="1c303-110">以下範例示範 `object` 類型的變數如何接受任何資料類型的值，以及 `object` 類型的變數如何從 .NET Framework 對 <xref:System.Object> 使用方法。</span><span class="sxs-lookup"><span data-stu-id="1c303-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a><span data-ttu-id="1c303-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="1c303-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1c303-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c303-112">See also</span></span>

- [<span data-ttu-id="1c303-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="1c303-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1c303-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1c303-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1c303-115">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="1c303-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1c303-116">參考型別</span><span class="sxs-lookup"><span data-stu-id="1c303-116">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="1c303-117">實值型別</span><span class="sxs-lookup"><span data-stu-id="1c303-117">Value Types</span></span>](value-types.md)
