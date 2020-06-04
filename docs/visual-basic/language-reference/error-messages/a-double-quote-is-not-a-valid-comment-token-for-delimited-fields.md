---
title: 在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_InvalidComment
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
ms.openlocfilehash: a66d43d249a12ffa552073866f2e0a1e6d453608
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409932"
---
# <a name="a-double-quote-is-not-a-valid-comment-token-for-delimited-fields-where-escapequote-is-set-to-true"></a>在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元

引號已提供為 `TextFieldParser`的分隔符號，但 `EscapeQuotes` 設為 `True`。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 將 `EscapeQuotes` 設定為 `False`。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- [作法：從逗號分隔文字檔讀取](../../developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
