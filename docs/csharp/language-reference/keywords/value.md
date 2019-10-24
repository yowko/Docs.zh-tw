---
title: value 內容關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: 34b192d17bd96b6b893c9f14f0d4a77274a32f78
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771748"
---
# <a name="value-c-reference"></a><span data-ttu-id="900bb-102">value (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="900bb-102">value (C# Reference)</span></span>

<span data-ttu-id="900bb-103">內容關鍵字 `value` 用於[屬性](../../programming-guide/classes-and-structs/properties.md)和[索引子](../../programming-guide/indexers/index.md)宣告的 `set` 存取子中。</span><span class="sxs-lookup"><span data-stu-id="900bb-103">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="900bb-104">它類似于方法的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="900bb-104">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="900bb-105">這個字 `value` 會參考用戶端程式代碼嘗試指派給屬性或索引子的值。</span><span class="sxs-lookup"><span data-stu-id="900bb-105">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="900bb-106">在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。</span><span class="sxs-lookup"><span data-stu-id="900bb-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="900bb-107">就用戶端程式碼的觀點而言，是以簡單指派寫入作業。</span><span class="sxs-lookup"><span data-stu-id="900bb-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="900bb-108">如需詳細資訊，請參閱[Properties](../../programming-guide/classes-and-structs/properties.md)和[Indexeres](../../programming-guide/indexers/index.md)文章。</span><span class="sxs-lookup"><span data-stu-id="900bb-108">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexeres](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="900bb-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="900bb-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="900bb-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="900bb-110">See also</span></span>

- [<span data-ttu-id="900bb-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="900bb-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="900bb-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="900bb-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="900bb-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="900bb-113">C# Keywords</span></span>](index.md)
