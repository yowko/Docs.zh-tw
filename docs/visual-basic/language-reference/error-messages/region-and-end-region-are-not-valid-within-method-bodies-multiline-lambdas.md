---
title: "'#Region' 與 ' #End Region' 陳述式在具有多行的方法主體中無效"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 5652139ab139ea93258eb116f97ba21b76986a24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400379"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>'#Region' 及 '#End Region' 陳述式在方法主體/多行 Lambda 中無效
`#Region`區塊必須在類別、模組或命名空間層級宣告。 可折迭的區域可以包含一或多個程式，但它無法在程式內開始或結束。  
  
 **錯誤識別碼：** BC32025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定先前的程式已使用或語句正確地終止 `End Function` `End Sub` 。  
  
2. 請確定和指示詞位於 `#Region` `#End Region` 相同的程式碼區塊中。  
  
## <a name="see-also"></a>另請參閱

- [#Region 指示詞](../directives/region-directive.md)
