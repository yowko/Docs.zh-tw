---
title: == 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: f8356320817771cb559192c1ce720a80bf33bbf9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>== 運算子 (C# 參考)
對於預先定義的實值型別，等號比較運算子 (`==`) 在運算元相等時傳回 true；否則傳回 `false`。 對於 [string](../../../csharp/language-reference/keywords/string.md) 以外的參考型別，若兩個運算元參考到同一物件，`==` 會傳回 `true`。 對於 `string` 類型，`==` 會比較字串的值。  
  
## <a name="remarks"></a>備註  
 使用者定義的實值型別可以多載 `==` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 使用者定義的參考型別也可以，不過 `==` 對預先定義和使用者定義之參考型別的預設運作方式會如上所述。 如果多載 `==`，也必須多載 [!=](../../../csharp/language-reference/operators/not-equal-operator.md)。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
