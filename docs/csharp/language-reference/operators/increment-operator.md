---
title: ++ 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274592"
---
# <a name="-operator-c-reference"></a>++ 運算子 (C# 參考)
遞增運算子 (`++`) 的運算元遞增量為 1。 遞增運算子可以出現在其運算元的前後： `++variable` 和 `variable++`。  
  
## <a name="remarks"></a>備註  
 第一種形式是前置詞遞增作業。 作業的結果是運算元已遞增之後的值。  
  
 第二種形式是後置遞增作業。 作業的結果是運算元遞增之前的值。  
  
 數字和列舉型別有預先定義的遞增運算子。 使用者定義類型可以多載 `++` 運算子。 整數類資料類型上的作業通常允許用於列舉型別。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
