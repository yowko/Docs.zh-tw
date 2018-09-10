---
title: '* 運算子 (C# 參考)'
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 873cc1dc0d81425117f1784353acf08b35158133
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44225356"
---
# <a name="-operator-c-reference"></a>* 運算子 (C# 參考)
乘法運算子 (`*`)，它會計算其運算元的乘積。 所有數字類型都有預先定義的乘法運算子。  

`*` 也可做為取值運算子，其允許讀取和寫入指標中。
  
## <a name="remarks"></a>備註  
 `*` 運算子也可以用來宣告指標類型，並對指標取值 (Dereference)。 此運算子只可用於 Unsafe 內容中，並透過使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字及需要 [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) 編譯器選項來表示。  取值運算子也稱作間接運算子。  
  
 使用者定義型別可以多載二進位 `*` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))。 二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。  
  
## <a name="example"></a>範例  
 [!code-csharp-interactive[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [C# 運算子](../../../csharp/language-reference/operators/index.md)
