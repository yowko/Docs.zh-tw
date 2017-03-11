---
title: "Documenting Your Code with XML (Visual Basic) | Microsoft Docs"
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
  - "XML, documenting code"
  - "XML comments, Visual Basic"
  - "Visual Basic code, documenting with XML"
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Documenting Your Code with XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中，您可以使用 XML 在程式碼中加入文件  
  
## XML 文件註解  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 提供了自動為專案建立 XML 文件的簡易方法。  您可以自動為型別和成員產生 XML 基本架構，然後提供摘要、每個參數的描述性文件，以及其他備註。  經過適當的設定，XML 文件就會以和專案相同的名稱及 .xml 副檔名，自動發出至 XML 檔。  如需詳細資訊，請參閱 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
 可以使用 XML 檔案，不然會當做 XML 來操作。  這個檔案與專案的輸出 .exe 或 .dll 檔案位於相同的目錄中。  
  
 以 `'''` 起始的 XML 文件。  處理這些註解有一些限制：  
  
-   文件必須依照語式正確 \(Well\-Formed\) XML 格式。  如果 XML 的語式不正確，便會產生一個警告，且文件檔會包含一段說明所發生錯誤的註解。  
  
-   開發者可以自由建立自己的標記集合。  有一組建議的標記 \(請參閱本主題中的＜相關章節＞一節\)。  某些建議的標記有特殊的意義：  
  
    -   \<param\> 標記是用來描述參數。  如果使用，編譯器會驗證該參數及所有描述於文件中的參數是否存在。  如果驗證失敗，編譯器會發出警告。  
  
    -   `cref` 屬性 \(Attribute\) 可以附加到任一個標記上，以提供程式碼項目的參考。  編譯器會驗證此程式碼項目是否存在。  如果驗證失敗，編譯器會發出警告。  在尋找 `cref` 屬性中描述的型別時，編譯器也會尊從任何 `Imports` 陳述式 \(Statement\)。  
  
    -   \<summary\> 標記是由 IntelliSense 在 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 中使用，以顯示型別或成員的其他資訊。  
  
## 相關章節  
 如需建立含文件註解之 XML 檔案的詳細資訊，請參閱下列主題：  
  
-   [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [Processing the XML File](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio 中的 XML 工具](/visual-studio/xml-tools/xml-tools-in-visual-studio)  
  
## 請參閱  
 [使用 Visual Basic 開發應用程式](../../../visual-basic/developing-apps/index.md)   
 [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)