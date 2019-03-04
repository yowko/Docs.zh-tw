---
title: 具名方法委派與匿名方法 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 8d3cecbaecc8cf5af1e06f29c9bb8a151523d3e8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970944"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>具名方法委派與匿名方法 (C# 程式設計手冊)
[delegate](../../../csharp/language-reference/keywords/delegate.md) 可以與具名方法產生關聯。 當您使用具名方法具現化委派時，方法會當做參數傳遞，例如：  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 這會使用具名方法呼叫。 使用具名方法建構的委派可封裝[靜態](../../../csharp/language-reference/keywords/static.md)方法或執行個體方法。 在舊版 C# 中，要具現化委派只能使用具名方法。 不過，如果建立新方法會產生額外不必要的負荷，C# 可讓您具現化委派，並立即指定呼叫委派時會處理的程式碼區塊。 區塊可以包含 Lambda 運算式或匿名方法。 如需詳細資訊，請參閱[匿名函式](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)。  
  
## <a name="remarks"></a>備註  
 當做委派參數傳遞的方法必須擁有與委派宣告相同的簽章。  
  
 委派執行個體可封裝靜態或執行個體方法。  
  
 即使委派可使用 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數，但仍不建議您用於多點傳送事件委派，因為無從得知將呼叫哪一個委派。  
  
## <a name="example-1"></a>範例 1  
 以下是宣告和使用委派的簡單範例。 請注意，委派 `Del` 和相關聯的方法 `MultiplyNumbers` 必須擁有相同的簽章  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>範例 2  
 在下列範例中，一個委派會同時對應到靜態和執行個體方法，並傳回每個方法的特定資訊。  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [委派](../../../csharp/programming-guide/delegates/index.md)
- [匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [如何：組合委派 (多點傳送委派)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
- [事件](../../../csharp/programming-guide/events/index.md)
