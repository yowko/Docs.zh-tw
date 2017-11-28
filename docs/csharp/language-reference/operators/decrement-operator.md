---
title: "-- 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4eb68143103d44defeac7191e7c4ce7d1ee90e9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="---operator-c-reference"></a>-- 運算子 (C# 參考)
遞減運算子 (`--`) 的運算元遞減量為 1。 遞減運算子可以出現在其運算元的前後：`--variable` 和 `variable--`。 第一種形式是前置遞減運算。 運算的結果是運算元遞減「之後」的值。 第二種形式是後置遞減運算。 運算的結果是運算元遞減「之前」的值。  
  
## <a name="remarks"></a>備註  
 數字和列舉型別有預先定義的遞減運算子。  
  
 使用者定義型別可以多載 `--` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
