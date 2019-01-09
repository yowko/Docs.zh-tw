---
title: value 內容關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- value_CSharpKeyword
helpviewer_keywords:
- value keyword [C#]
ms.assetid: c99d6468-687f-4a46-89b4-a95e1b00bf6d
ms.openlocfilehash: ee80888a57e999fa44e891dd6e0d64caa698009c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612058"
---
# <a name="value-c-reference"></a><span data-ttu-id="43e8d-102">value (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="43e8d-102">value (C# Reference)</span></span>

<span data-ttu-id="43e8d-103">內容關鍵字 `value` 用於一般屬性宣告中的 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="43e8d-103">The contextual keyword `value` is used in the set accessor in ordinary property declarations.</span></span> <span data-ttu-id="43e8d-104">類似於方法的輸入參數。</span><span class="sxs-lookup"><span data-stu-id="43e8d-104">It is similar to an input parameter on a method.</span></span> <span data-ttu-id="43e8d-105">`value` 一字參考用戶端程式碼嘗試指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="43e8d-105">The word `value` references the value that client code is attempting to assign to the property.</span></span> <span data-ttu-id="43e8d-106">在下例中，`MyDerivedClass` 具有稱為 `Name` 的屬性，它使用 `value` 參數將新的字串指派給支援欄位 `name`。</span><span class="sxs-lookup"><span data-stu-id="43e8d-106">In the following example, `MyDerivedClass` has a property called `Name` that uses the `value` parameter to assign a new string to the backing field `name`.</span></span> <span data-ttu-id="43e8d-107">就用戶端程式碼的觀點而言，是以簡單指派寫入作業。</span><span class="sxs-lookup"><span data-stu-id="43e8d-107">From the point of view of client code, the operation is written as a simple assignment.</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="43e8d-108">如需使用 `value` 的詳細資訊，請參閱[屬性](../../programming-guide/classes-and-structs/properties.md)。</span><span class="sxs-lookup"><span data-stu-id="43e8d-108">For more information about the use of `value`, see [Properties](../../programming-guide/classes-and-structs/properties.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="43e8d-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="43e8d-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="43e8d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43e8d-110">See also</span></span>

- [<span data-ttu-id="43e8d-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="43e8d-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="43e8d-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="43e8d-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="43e8d-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="43e8d-113">C# Keywords</span></span>](index.md)