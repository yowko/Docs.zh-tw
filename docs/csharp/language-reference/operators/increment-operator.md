---
title: ++ 運算子 (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6deb2f772fefc93020e7eaaed6be35e48b11df7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>++ 運算子 (C# 參考)
遞增運算子 (`++`) 的運算元遞增量為 1。 遞增運算子可以出現在其運算元的前後： `++variable` 和 `variable++`。  
  
## <a name="remarks"></a>備註  
 第一種形式是前置詞遞增作業。 作業的結果是運算元已遞增之後的值。  
  
 第二種形式是後置遞增作業。 作業的結果是運算元遞增之前的值。  
  
 數字和列舉型別有預先定義的遞增運算子。 使用者定義類型可以多載 `++` 運算子。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
