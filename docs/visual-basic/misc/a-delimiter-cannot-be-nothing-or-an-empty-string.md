---
title: "分隔符號不可以是 Nothing 或空字串 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_DelimiterNothing"
ms.assetid: 8885fcd1-c201-409d-9a32-6ff2b13c0c13
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# 分隔符號不可以是 Nothing 或空字串
`TextFieldParser` 無法讀取自檔案，因為 `Delimiters` 屬性設定為 `Nothing` 或為空白 `String` \(""\)。  
  
### 更正這個錯誤  
  
-   請提供 `Delimiters` 的有效值。  
  
## 請參閱  
 [TextFieldParser.SetDelimiters 方法](http://msdn.microsoft.com/zh-tw/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [TextFieldParser.Delimiters 屬性](http://msdn.microsoft.com/zh-tw/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [How to: Read From Comma\-Delimited Text Files](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [TextFieldParser Object](../../visual-basic/language-reference/objects/textfieldparser-object.md)   
 [Parsing Text Files with the TextFieldParser Object](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)