---
title: "當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b5ee30da2146d6fa9841a80cc0e841bd737961f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。
`TextFieldParser` 無法從檔案讀取，因為引號 (") 已供做分隔符號且 `EscapeQuotes` 設為 `True`。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請設定 `EscapeQuotes` 為 `False`。  
  
## <a name="see-also"></a>請參閱  
 [TextFieldParser.SetDelimiters 方法](http://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [TextFieldParser.Delimiters Property](http://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [如何：從逗號分隔文字檔讀取](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [TextFieldParser 物件](../../visual-basic/language-reference/objects/textfieldparser-object.md)
