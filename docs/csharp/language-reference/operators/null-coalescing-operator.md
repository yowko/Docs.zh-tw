---
title: ?? 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8fa751654acaf5939fb8f8068c7323e365f7bdab
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
ms.locfileid: "34458096"
---
# <a name="-operator-c-reference"></a>?? 運算子 (C# 參考)
`??` 運算子稱為 null 聯合運算子。  如果運算元不是 null，則會傳回左方運算元，否則傳回右方運算元。  
  
## <a name="remarks"></a>備註  
 可為 Null 的類型可以表示來自類型網域的值，或值可以是未定義 (這種情況下，值為 null)。 當左方運算元是可為 Null 的型別且其值為 null 時，您可使用 `??` 運算子的語法表達能力傳回適當的值 (右方運算元)。 如果您嘗試在不使用 `??` 運算子的情況下，將可為 null 的實值類型指派給不可為 null 的實值類型，則會產生編譯時期錯誤。 如果您使用轉型，而可為 null 的實值類型目前為未定義，則會擲回 `InvalidOperationException` 例外狀況。  
  
 如需詳細資訊，請參閱[可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)。  
  
 ?? 運算子的結果 不視為常數，即使它的兩個引數都是常數。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)  
 [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)  
 [「增益」(Lift) 的真正意義是什麼？](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
