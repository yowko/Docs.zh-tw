---
title: "-- 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 17
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
ms.openlocfilehash: 100e68f3b07164b0cfb398a32f47137f2726943f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="---operator-c-reference"></a>-- 運算子 (C# 參考)
遞減運算子 (`--`) 的運算元遞減量為 1。 遞減運算子可以出現在其運算元的前後：`--variable` 和 `variable--`。 第一種形式是前置遞減運算。 運算的結果是運算元遞減「之後」的值。 第二種形式是後置遞減運算。 運算的結果是運算元遞減「之前」的值。  
  
## <a name="remarks"></a>備註  
 數字和列舉型別有預先定義的遞減運算子。  
  
 使用者定義型別可以多載 `--` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 整數類資料類型上的作業通常允許用於列舉類型。  
  
## <a name="example"></a>範例  
 [!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)

