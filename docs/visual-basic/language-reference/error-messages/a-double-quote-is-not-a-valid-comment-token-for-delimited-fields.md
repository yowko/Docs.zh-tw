---
title: 在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5677ee7415fe385805413ccbdec20762ac0573a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元
引號已提供為 `TextFieldParser`的分隔符號，但 `EscapeQuotes` 設為 `True`。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請設定 `EscapeQuotes` 為 `False`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>  
 [如何：從逗號分隔文字檔讀取](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
