---
title: "Parsing Text Files with the TextFieldParser Object (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "TextFieldParser object, using"
  - "I/O [Visual Basic], parsing files"
  - "files, parsing"
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Parsing Text Files with the TextFieldParser Object (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`TextFieldParser` 物件可讓您剖析和處理非常大的檔案 \(而此種檔案的結構為以寬度分隔的文字資料行\)，例如記錄檔或舊版資料庫資訊。  以 `TextFieldParser` 剖析文字檔類似於逐一查看文字檔內容，而用於擷取文字欄位的剖析方法，則類似用於語彙基元化已分隔字串的字串操作方法。  
  
## 剖析不同類型的文字檔  
 文字檔可能會具有各種寬度的欄位，並以字元分隔，例如逗號或定位鍵空格。  請定義 `TextFieldType` 和分隔符號 \(Delimiter\)，如以下範例所示，這個範例會使用 `SetDelimiters` 方法，定義以定位鍵分隔的文字檔：  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/visualbasic/parsing-text-files-with-_1.vb)]  
  
 其他的文字檔可能會具有固定寬度的欄位。  在這種情況下，您必須將 `TextFieldType` 定義為 `FixedWidth`，並定義每個欄位的寬度，如以下範例所示。  這個範例會使用 `SetFieldWidths` 方法定義文字的資料行：第一個資料行為 5 個字元寬、第二個為 10 個字元寬、第三個為 11 個字元寬，而第四個資料行的寬度則是可變動的。  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/visualbasic/parsing-text-files-with-_2.vb)]  
  
 定義格式之後，您就可以在檔案上執行迴圈 \(Loop\)，使用 `ReadFields` 方法依序處理每一行。  
  
 如果欄位和指定的格式不相符，則會擲回 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> 例外狀況。  擲回這類例外狀況時，`ErrorLine` 和 `ErrorLineNumber` 屬性會保留造成例外狀況的文字和該文字的行號。  
  
## 剖析具有多種格式的檔案  
 開始讀取欄位之前，可以先用 `TextFieldParser` 物件的 `PeekChars` 方法進行檢查，這讓您可以為欄位定義多種格式，據以做出適當回應。  如需詳細資訊，請參閱 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>   
 [疑難排解例外狀況：Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)