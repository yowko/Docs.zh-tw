---
title: '% 運算子 (C# 參考)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 796b4a40347fc5881db27a8a8a28404c7c4e8c5b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a>% 運算子 (C# 參考)
remainder 運算子 (`%`) 會計算其第一個運算元除以第二個運算元之後的餘數。 所有數值類型都有預先定義的餘數運算子。 
  
## <a name="remarks"></a>備註  
 公式 `a % b` 一律會傳回範圍 `(-b, b)` 中的值、不含上下界值 (它永遠不會傳回 `b` 或 `-b`)，並保留被除數的正負號。 針對整數除法，餘數運算子會滿足規則 `a % b = a - (a / b) * b`。
  
 這不能與標準模數混淆，標準模數符合類似的規則，但是使用浮點除法並傳回範圍 `[0, b)` 中的值。 C# 沒有標準模數的運算子。 不過，正值被除數的行為是一樣的。
  
 使用者定義型別可以多載 `%` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>註解  
 請注意與 double 類型建立關聯的四捨五入錯誤。  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
