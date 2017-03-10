---
title: "當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_IllegalDelimiter"
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# 當 EscapeQuotes 設定為 True 時，因為雙引號不是合法的分隔符號，所以無法讀取分隔的欄位。
`TextFieldParser` 無法從檔案讀取，因為引號 \("\) 已供做分隔符號且 `EscapeQuotes` 設為 `True`。  
  
### 更正這個錯誤  
  
-   請設定 `EscapeQuotes` 為 `False`。  
  
## 請參閱  
 [TextFieldParser.SetDelimiters 方法](http://msdn.microsoft.com/zh-tw/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [TextFieldParser.Delimiters 屬性](http://msdn.microsoft.com/zh-tw/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [How to: Read From Comma\-Delimited Text Files](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [TextFieldParser Object](../../visual-basic/language-reference/objects/textfieldparser-object.md)