---
title: '&#39; #Region &#39;和 &#39; #End 區域 &#39;陳述式不是在方法主體多行 lambda 中無效'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39; #Region &#39;和 &#39; #End 區域 &#39;陳述式不是在方法主體/多行 lambda 中無效
`#Region`區塊必須宣告類別、 模組或命名空間層級。 可摺疊的區域可以包含一或多個程序，但它無法開始或結束程序內。  
  
 **錯誤 ID:** BC32025  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定前面的程序已正確地終止與`End Function`或`End Sub`陳述式。  
  
2.  請確認`#Region`和`#End Region`指示詞是在相同的程式碼區塊。  
  
## <a name="see-also"></a>另請參閱  
 [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)
