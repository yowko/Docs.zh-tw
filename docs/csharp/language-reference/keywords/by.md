---
title: by 內容關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- by
- by_CSharpKeyword
helpviewer_keywords:
- by keyword [C#]
ms.assetid: efe6f0e3-be40-4df2-a144-c7db968ae052
ms.openlocfilehash: 23daf2aaf5d9456c76c5b2ac889243b1ed31b077
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602219"
---
# <a name="by-c-reference"></a><span data-ttu-id="94922-102">by (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="94922-102">by (C# Reference)</span></span>

<span data-ttu-id="94922-103">`by` 內容關鍵字可用於查詢運算式的 `group` 子句，以指定應如何將傳回的項目分組。</span><span class="sxs-lookup"><span data-stu-id="94922-103">The `by` contextual keyword is used in the `group` clause in a query expression to specify how the returned items should be grouped.</span></span> <span data-ttu-id="94922-104">如需詳細資訊，請參閱 [group 子句](./group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="94922-104">For more information, see [group clause](./group-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="94922-105">範例</span><span class="sxs-lookup"><span data-stu-id="94922-105">Example</span></span>

<span data-ttu-id="94922-106">下列範例示範如何在 `group` 子句中使用 `by` 內容關鍵字，以指定應根據每個學生姓氏的第一個字母將學生分組。</span><span class="sxs-lookup"><span data-stu-id="94922-106">The following example shows the use of the `by` contextual keyword in a `group` clause to specify that the students should be grouped according to the first letter of the last name of each student.</span></span>

[!code-csharp[csrefKeywordsContextual#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#10)]

## <a name="see-also"></a><span data-ttu-id="94922-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94922-107">See also</span></span>

- [<span data-ttu-id="94922-108">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="94922-108">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
