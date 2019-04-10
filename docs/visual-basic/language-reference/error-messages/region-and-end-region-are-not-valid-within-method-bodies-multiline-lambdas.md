---
title: "'#Region' 和 ' #End Region' 陳述式不是在方法主體 / 多行 lambda 中無效"
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c41b95da7e3565ae7aaf332fe49361336e79f7c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303904"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>'#Region' 及 '#End Region' 陳述式在方法主體/多行 Lambda 中無效
`#Region`區塊必須宣告類別、 模組或命名空間層級。 可摺疊的區域可以包含一或多個程序，但不是能開始或結束程序內。  
  
 **錯誤 ID:** BC32025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 確保與前述程序已正確地終止`End Function`或`End Sub`陳述式。  
  
2. 請確認`#Region`和`#End Region`指示詞是在相同的程式碼區塊。  
  
## <a name="see-also"></a>另請參閱

- [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)
