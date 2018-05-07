---
title: 在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: 5838ef168523e8ba31fe5db93781bc409690e7ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
