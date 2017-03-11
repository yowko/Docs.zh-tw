---
title: "在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_InvalidComment"
dev_langs: 
  - "VB"
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# 在 EscapeQuote 設定為 True 的情況下，雙引號不是用於分隔欄位的有效註解語彙基元
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

引號已提供為 `TextFieldParser` 的分隔符號，但 `EscapeQuotes` 設為 `True`。  
  
### 更正這個錯誤  
  
-   請設定 `EscapeQuotes` 為 `False`。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 [How to: Read From Comma\-Delimited Text Files](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)