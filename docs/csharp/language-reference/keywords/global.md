---
title: global (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ed2acc7384fbf3825a304888c58658d082858211
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2017
---
# <a name="global-c-reference"></a><span data-ttu-id="537bb-102">global (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="537bb-102">global (C# Reference)</span></span>
<span data-ttu-id="537bb-103">當 `global` 內容關鍵字出現在 [:: 運算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md) 之前時，是指全域命名空間，這是所有 C# 程式的預設命名空間，不然就是不具名。</span><span class="sxs-lookup"><span data-stu-id="537bb-103">The `global` contextual keyword, when it comes before the [:: operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="537bb-104">如需詳細資訊，請參閱[如何：使用全域命名空間別名](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)。</span><span class="sxs-lookup"><span data-stu-id="537bb-104">For more information, see [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="537bb-105">範例</span><span class="sxs-lookup"><span data-stu-id="537bb-105">Example</span></span>  
 <span data-ttu-id="537bb-106">下列範例示範如何使用 `global` 內容關鍵字，指定在全域命名空間中定義類別 `TestApp`：</span><span class="sxs-lookup"><span data-stu-id="537bb-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/global_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="537bb-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="537bb-107">See Also</span></span>  
 [<span data-ttu-id="537bb-108">命名空間</span><span class="sxs-lookup"><span data-stu-id="537bb-108">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
