---
title: 當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: 66116e6f3d8338db3884cd375aeb880930c8d861
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639281"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。
`TextFieldParser` 無法從檔案讀取，因為引號 (") 已供做分隔符號且 `EscapeQuotes` 設為 `True`。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   請設定 `EscapeQuotes` 為 `False`。  
  
## <a name="see-also"></a>另請參閱  
 [TextFieldParser.SetDelimiters 方法](http://msdn.microsoft.com/library/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)  
 [TextFieldParser.Delimiters 屬性](http://msdn.microsoft.com/library/4eb18f4d-3011-40a9-b668-be93eed0444f)  
 [如何：從逗號分隔文字檔讀取](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [TextFieldParser 物件](../../visual-basic/language-reference/objects/textfieldparser-object.md)
