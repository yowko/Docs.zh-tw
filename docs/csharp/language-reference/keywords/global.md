---
title: global 內容關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 1c0177c52e21ae60477a283085a2893e2e067c54
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633471"
---
# <a name="global-c-reference"></a><span data-ttu-id="e6b59-102">global (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e6b59-102">global (C# Reference)</span></span>

<span data-ttu-id="e6b59-103">當 `global` 內容關鍵字出現在 [:: 運算子](../operators/namespace-alias-qualifer.md) 之前時，是指全域命名空間，這是所有 C# 程式的預設命名空間，不然就是不具名。</span><span class="sxs-lookup"><span data-stu-id="e6b59-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="e6b59-104">如需詳細資訊，請參閱[如何：使用全域命名空間別名](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="e6b59-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="e6b59-105">範例</span><span class="sxs-lookup"><span data-stu-id="e6b59-105">Example</span></span>

<span data-ttu-id="e6b59-106">下列範例示範如何使用 `global` 內容關鍵字，指定在全域命名空間中定義類別 `TestApp`：</span><span class="sxs-lookup"><span data-stu-id="e6b59-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="e6b59-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6b59-107">See also</span></span>

- [<span data-ttu-id="e6b59-108">命名空間</span><span class="sxs-lookup"><span data-stu-id="e6b59-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
