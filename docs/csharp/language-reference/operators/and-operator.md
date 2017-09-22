---
title: "&amp; 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d92a860df6fcc9acf14aab4ec558556735ac8aac
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="amp-operator-c-reference"></a>&amp; 運算子 (C# 參考)
& 運算子可以作為一元或二元運算子。  
  
## <a name="remarks"></a>備註  
 一元 & 運算子會傳回運算元的位址 (需要 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容)。  
  
 整數型別和 `bool` 會預先定義二元 & 運算子。 對於整數型別，& 會計算其運算元的邏輯位元 AND。 對於 `bool` 運算元，& 會計算其運算元的邏輯 AND；亦即，如果且唯有當其兩個運算元都是 `true` 時，結果會是 `true`。  
  
 不論第一個運算子的值為何，`&` 運算子都會評估兩個運算子。 例如:   
  
 [!code-cs[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 使用者定義型別可以多載二進位 `&` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 整數類資料類型上的作業通常允許用於列舉型別。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。  
  
## <a name="example"></a>範例  
 [!code-cs[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 運算子](../../../csharp/language-reference/operators/index.md)

