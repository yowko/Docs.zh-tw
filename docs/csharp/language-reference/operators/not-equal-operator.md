---
title: "!= 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '!=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
caps.latest.revision: 14
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
ms.openlocfilehash: 49c5c9668c6b1169220ee4fa0babf167292a9813
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>!= 運算子 (C# 參考)
不等比較運算子 (`!=`) 會在其運算元相等時傳回 false，否則傳回 true。 所有類型 (包括字串和物件) 已預先定義不等比較運算子。 使用者定義型別可以多載 `!=` 運算子。  
  
## <a name="remarks"></a>備註  
 對於預先定義的實值型別，不等比較運算子 (`!=`) 在其運算元的值不同時傳回 true；否則傳回 false。 對於 `string` 以外的參考型別，若 `!=` 的兩個運算元參考不同物件，則會傳回 true。 對於 `string` 類型，`!=` 會比較字串的值。  
  
 使用者定義的實值型別可以多載 `!=` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 使用者定義的參考型別也可以，不過 `!=` 對預先定義和使用者定義之參考型別的預設運作方式會如上所述。 如果多載 `!=`，也必須多載 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md)。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-cs[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)

