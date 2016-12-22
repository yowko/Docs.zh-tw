---
title: "/doc | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "doc compiler option [Visual Basic]"
  - "-doc compiler option [Visual Basic]"
  - "/doc compiler option [Visual Basic]"
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /doc
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

將文件註解處理成 XML 檔案。  
  
## 語法  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`+`  &#124; `-`|選擇項。  指定 \+ 或只是 `/doc`，讓編譯器產生文件資訊，並將其置於 XML 檔案。  指定 `-`  是未指定 `/doc` 的對等用法，因而無法建立文件資訊。|  
|`file`|如果使用 `/doc:`，則為必要項。  指定 XML 輸出檔，它會填入編譯之原始程式碼檔內的註解。  如果檔案名稱包含空格，請將名稱放在引號 \(" "\) 中。|  
  
## 備註  
 `/doc` 選項會控制編譯器是否產生含有文件註解的 XML 檔案。  如果使用 `/doc:``file` 語法，則 `file` 參數會指定 XML 檔案的名稱。  如果使用 `/doc` 或 `/doc+`，則編譯器會從編譯器正在建立的可執行檔或程式庫中取得 XML 檔案名稱。  如果使用 `/doc-` 或未指定 `/doc` 選項，則編譯器不會建立 XML 檔案。  
  
 在原始程式碼檔案中，文件註解可在下列定義之前：  
  
-   使用者定義的型別 \(例如，[類別](../../../visual-basic/language-reference/statements/class-statement.md)或[介面](../../../visual-basic/language-reference/statements/interface-statement.md)\)  
  
-   成員 \(例如，欄位、[事件](../../../visual-basic/language-reference/statements/event-statement.md)、[屬性](../../../visual-basic/language-reference/statements/property-statement.md)、[函式](../../../visual-basic/language-reference/statements/function-statement.md)或[副程式](../../../visual-basic/language-reference/statements/sub-statement.md)\)。  
  
 若要將產生的 XML 檔案與 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] [IntelliSense](/visual-studio/ide/using-intellisense) 功能搭配使用，請讓 XML 檔案的檔名與想要支援的組件相同。  確定 XML 檔案與組件位於相同目錄中，以便在 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 專案中參考組件時，也會找到 .xml 檔案。  若要讓 IntelliSense 針對專案或專案所參考之專案內的程式碼運作，不需要 XML 文件檔案。  
  
 除非使用 `/target:module` 進行編譯，否則 XML 檔案會包含標記 `<assembly></assembly>`。  這些標記會指定檔案名稱，此檔案含有編譯輸出檔的組件資訊清單。  
  
 請參閱[XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)，以取得從程式碼中註解產生文件的方法。  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/doc|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  在 \[**產生 XML 文件檔案**\] 方塊中設定值。|  
  
## 範例  
 請參閱[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) 中的範例。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)