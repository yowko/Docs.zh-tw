---
title: by 內容關鍵字 - C# 參考
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: 4fa32a0dbfd8210ef8537aee849a55414b107a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713724"
---
# <a name="by-c-reference"></a><span data-ttu-id="dd506-102">by (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="dd506-102">by (C# Reference)</span></span>

<span data-ttu-id="dd506-103">`by` 內容關鍵字可用於查詢運算式的 `group` 子句，以指定應如何將傳回的項目分組。</span><span class="sxs-lookup"><span data-stu-id="dd506-103">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="dd506-104">有關詳細資訊，請參閱[組子句](./group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="dd506-104">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="dd506-105">範例</span><span class="sxs-lookup"><span data-stu-id="dd506-105">Example</span></span>

<span data-ttu-id="dd506-106">下列範例示範如何在 `group` 子句中使用 `by` 內容關鍵字，以指定應根據每個學生姓氏的第一個字母將學生分組。</span><span class="sxs-lookup"><span data-stu-id="dd506-106">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="dd506-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd506-107">See also</span></span>

- [<span data-ttu-id="dd506-108">C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="dd506-108">LINQ in C#</span></span>](../../linq/index.md)
