---
title: "^ 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 19
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
ms.openlocfilehash: f081dd2979930404639638179444adc05dd462e1
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a>^ 運算子 (C# 參考)
整數型別和 `bool` 會預先定義二元 `^` 運算子。 對於整數型別，`^` 會計算其運算元的位元互斥 OR。 對於 `bool` 運算元，`^` 會計算其運算元的邏輯位元互斥 OR；亦即，如果且唯有在正好其中一個運算元是 `true` 時，結果會是 `true`。  
  
## <a name="remarks"></a>備註  
 使用者定義型別可以多載 `^` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-cs[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 前一個範例中的 `0xf8 ^ 0x3f` 計算會執行下列兩個二進位值的位元互斥 OR，這兩個值對應於十六進位值 F8 和 3F：  
  
 `1111 1000`  
  
 `0011 1111`  
  
 互斥 OR 的結果是 `1100 0111`，這是十六進位的 C7。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)

