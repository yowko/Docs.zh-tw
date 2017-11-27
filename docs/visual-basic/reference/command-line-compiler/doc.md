---
title: /doc
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2490529b951ef6e583e3bfa54afced89c823e874
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="doc"></a>/doc
將文件註解處理成 XML 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
/doc[+ | -]  
' -or-  
/doc:file  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇項。 指定 +，或簡稱`/doc`，會導致編譯器產生文件資訊，並將它放在 XML 檔案。 指定`-`就相當於不指定`/doc`，導致建立沒有文件資訊。|  
|`file`|如果使用 `/doc:`，則為必要項。 指定輸出 XML 檔案，它會填入從編譯的原始程式碼檔案的註解。 如果檔案名稱包含空格，括住的名稱加上引號 ("")。|  
  
## <a name="remarks"></a>備註  
 `/doc`選項會控制是否編譯器會產生包含文件註解的 XML 檔案。 如果您使用`/doc:``file`語法，`file`參數會指定 XML 檔案的名稱。 如果您使用`/doc`或`/doc+`，編譯器會從可執行檔或編譯器所建立的文件庫中取得的 XML 檔案名稱。 如果您使用`/doc-`或不指定`/doc`選項，編譯器不會建立 XML 檔案。  
  
 在原始程式檔中，文件註解可以出現之前的定義如下：  
  
-   使用者定義類型，例如[類別](../../../visual-basic/language-reference/statements/class-statement.md)或[介面](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   成員，例如欄位、[事件](../../../visual-basic/language-reference/statements/event-statement.md)，[屬性](../../../visual-basic/language-reference/statements/property-statement.md)，[函式](../../../visual-basic/language-reference/statements/function-statement.md)，或[副程式](../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
 若要使用產生的 XML 檔案，與[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense)功能，可讓您想要支援的組件相同的 XML 檔案的檔案名稱。 請確認 XML 檔案位於與組件相同的目錄，以便組件中的參考時[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]專案的.xml 檔案位於以及。 XML 文件檔並不需要在單一專案或專案所參考的專案中的程式碼的 IntelliSense。  
  
 除非您使用編譯`/target:module`，XML 檔案包含標記`<assembly></assembly>`。 這些標記會指定包含編譯輸出檔的組件資訊清單之檔案的名稱。  
  
 請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)的方式來產生文件從您的程式碼中的註解。  
  
|在 Visual Studio 中設定 /doc 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [編譯] 索引標籤。<br />3.設定中的值**產生 XML 文件檔**方塊。|  
  
## <a name="example"></a>範例  
 請參閱[記載您的程式碼使用 XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)範例。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
