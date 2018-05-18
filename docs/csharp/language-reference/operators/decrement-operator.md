---
title: -- 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 25f301bc0b2bc9bf51b0a44f26b2efabae00e452
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="---operator-c-reference"></a>-- 運算子 (C# 參考)
遞減運算子 (`--`) 的運算元遞減量為 1。 遞減運算子可以出現在其運算元的前後：`--variable` 和 `variable--`。 第一種形式是前置遞減運算。 運算的結果是運算元遞減「之後」的值。 第二種形式是後置遞減運算。 運算的結果是運算元遞減「之前」的值。  
  
## <a name="remarks"></a>備註  
 數字和列舉型別有預先定義的遞減運算子。  
  
 使用者定義型別可以多載 `--` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
