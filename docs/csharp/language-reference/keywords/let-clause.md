---
title: "let 子句 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
dev_langs:
- CSharp
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 37ec0cb0c8c374a0b5250d82e880c96696b5584a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="let-clause-c-reference"></a>let 子句 (C# 參考)
在查詢運算式中，有時它十分適合儲存子運算式的結果，以將它用於後續子句。 您可以使用 `let` 關鍵字執行這項作業，而此關鍵字會建立新的範圍變數，並使用您提供的運算式結果將它初始化。 使用值初始化之後，就不能使用範圍變數來儲存另一個值。 不過，如果範圍變數保留可查詢類型，則可以進行查詢。  
  
## <a name="example"></a>範例  
 在下列範例中，以兩種方式使用 `let`：  
  
1.  建立本身可進行查詢的可列舉類型。  
  
2.  讓查詢只對範圍變數 `word` 呼叫一次 `ToLower`。 如果不使用 `let`，則您需要在 `where` 子句的每個述詞中呼叫 `ToLower`。  
  
 [!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [查詢關鍵字 (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [LINQ 查詢運算式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [開始使用 C# 中的 LINQ](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [如何：處理查詢運算式中的例外狀況](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)

