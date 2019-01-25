---
title: '&#39;#Region&#39;和&#39;#End 區域&#39;陳述式不是在方法主體 / 多行 lambda 中無效'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 55399cd123ce4d67cc833f2eabe3230acdafc0bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737211"
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39;和&#39;#End 區域&#39;陳述式不是在方法主體/多行 lambda 中無效
`#Region`區塊必須宣告類別、 模組或命名空間層級。 可摺疊的區域可以包含一或多個程序，但不是能開始或結束程序內。  
  
 **錯誤 ID:** BC32025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  確保與前述程序已正確地終止`End Function`或`End Sub`陳述式。  
  
2.  請確認`#Region`和`#End Region`指示詞是在相同的程式碼區塊。  
  
## <a name="see-also"></a>另請參閱
- [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)
