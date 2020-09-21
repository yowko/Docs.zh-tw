---
description: value 內容關鍵字 - C# 參考
title: value 內容關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ad2eb6f12d8c295dc5203994d6c570cd2377e3ee
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828912"
---
# <a name="value-c-reference"></a><span data-ttu-id="20a35-103">value (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="20a35-103">value (C# Reference)</span></span>

<span data-ttu-id="20a35-104">內容關鍵字可 `value` 用於 `set` [屬性](../../programming-guide/classes-and-structs/properties.md) 和 [索引子](../../programming-guide/indexers/index.md) 宣告中的存取子。</span><span class="sxs-lookup"><span data-stu-id="20a35-104">The contextual keyword `value` is used in the `set` accessor in [property](../../programming-guide/classes-and-structs/properties.md) and [indexer](../../programming-guide/indexers/index.md) declarations.</span></span> <span data-ttu-id="20a35-105">它類似于方法的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="20a35-105">It is similar to an input parameter of a method.</span></span> <span data-ttu-id="20a35-106">單字 `value` 參考用戶端程式代碼嘗試指派給屬性或索引子的值。</span><span class="sxs-lookup"><span data-stu-id="20a35-106">The word `value` references the value that client code is attempting to assign to the property or indexer.</span></span> <span data-ttu-id="20a35-107">在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。</span><span class="sxs-lookup"><span data-stu-id="20a35-107">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="20a35-108">就用戶端程式碼的觀點而言，是以簡單指派寫入作業。</span><span class="sxs-lookup"><span data-stu-id="20a35-108">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="20a35-109">如需詳細資訊，請參閱 [屬性](../../programming-guide/classes-and-structs/properties.md) 和 [索引子](../../programming-guide/indexers/index.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="20a35-109">For more information, see the [Properties](../../programming-guide/classes-and-structs/properties.md) and [Indexers](../../programming-guide/indexers/index.md) articles.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="20a35-110">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="20a35-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="20a35-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20a35-111">See also</span></span>

- [<span data-ttu-id="20a35-112">C # 參考</span><span class="sxs-lookup"><span data-stu-id="20a35-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="20a35-113">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="20a35-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="20a35-114">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="20a35-114">C# Keywords</span></span>](index.md)
