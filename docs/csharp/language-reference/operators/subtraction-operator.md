---
title: '- 運算子 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 315d8cf47cc0819e124c1c08546ede580918f328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-c-reference"></a>- 運算子 (C# 參考)
`-` 運算子可以作為一元或二元運算子。  
  
## <a name="remarks"></a>備註  
 會預先定義所有數字類型的一元 `-` 運算子。 對數值類型執行一元 `-` 運算的結果就是運算元的負數值。  
  
 針對所有數值和列舉類型預先定義二元 `-` 運算子，以將第一個運算元減去第一個運算元。  
  
 委派類型也會提供可執行委派移除的二元 `-` 運算子。  
  
 使用者定義型別可以多載一元 `-` 和二元 `-` 運算子。 如需詳細資訊，請參閱 [operator (C# 參考)](../../../csharp/language-reference/keywords/operator.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-operator_1.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 運算子](../../../csharp/language-reference/operators/index.md)
