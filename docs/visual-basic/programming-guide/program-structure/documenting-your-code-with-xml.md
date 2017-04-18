---
title: "記錄程式碼與 XML (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML, documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2ec4907ff96a0861f97de21bdf45662c558d0a95
ms.lasthandoff: 03/13/2017

---
# <a name="documenting-your-code-with-xml-visual-basic"></a>使用 XML 在程式碼中加入文件 (Visual Basic)
在[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]，您可以將您的程式碼使用 XML 文件  
  
## <a name="xml-documentation-comments"></a>XML 文件註解  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供簡單的方法，自動建立專案的 XML 文件。 您可以自動產生的 XML 基本架構型別和成員，然後再提供摘要、 描述性的文件的每個參數，以及其他備註。 適當的安裝程式，XML 文件就會自動發出至具有相同名稱做為您的專案，而且副檔名為.xml 的 XML 檔案。 如需詳細資訊，請參閱[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
 可以取用或其他方式操作它做為 XML 的 XML 檔案。 這個檔案位於與您的專案輸出.exe 或.dll 檔相同的目錄。  
  
 XML 文件開頭`'''`。 處理這些註解有一些限制︰  
  
-   文件必須格式正確 XML。 如果 XML 的格式不正確，則會產生警告，而且文件檔案包含註解指出發現錯誤。  
  
-   開發人員可以自由建立自己的標記集合。 沒有一組建議的標記 （請參閱本主題中的 < 相關章節 >）。 有些建議的標記有特殊意義︰  
  
    -   \<Param > 標記用來描述參數。 如果使用，則編譯器會驗證參數存在，並且所有的參數會在文件中描述。 如果驗證失敗，編譯器會發出警告。  
  
    -   `cref`屬性可以附加至任何標記以提供程式碼項目的參考。 編譯器會驗證此程式碼項目存在。 如果驗證失敗，編譯器會發出警告。 編譯器也會遵守任何`Imports`陳述式時搜尋類型中所述`cref`屬性。  
  
    -   \<摘要 > 中的 IntelliSense 即可使用標記[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]來顯示型別或成員的其他資訊。  
  
## <a name="related-sections"></a>相關章節  
 如需建立 XML 檔案與文件註解的詳細資訊，請參閱下列主題︰  
  
-   [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [處理 XML 檔案](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [Visual Studio 中的 XML 工具](https://docs.microsoft.com/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a>另請參閱  
 [使用 Visual Basic 開發應用程式](../../../visual-basic/developing-apps/index.md)   
 [Visual Basic 程式設計指南](../../../visual-basic/programming-guide/index.md)
