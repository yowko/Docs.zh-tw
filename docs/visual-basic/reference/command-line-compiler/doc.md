---
title: "/doc |Microsoft 文件"
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
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 1054eb256eb7670ee0454b02fc094e0306c1218d
ms.lasthandoff: 03/13/2017

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
|`+` &#124; `-`|選擇項。 指定 +，或只是`/doc`，會使編譯器產生文件資訊，並將它放在 XML 檔案。 指定`-`相當於未指定`/doc`，造成要建立文件資訊。|  
|`file`|如果使用 `/doc:`，則為必要項。 指定輸出 XML 檔案，它會填入從編譯的原始程式檔的註解。 如果檔案名稱包含空格，請用的名稱加上引號 ("")。|  
  
## <a name="remarks"></a>備註  
 `/doc`選項會控制是否編譯器會產生包含文件註解的 XML 檔案。 如果您使用`/doc:``file`語法，`file`參數會指定 XML 檔案的名稱。 如果您使用`/doc`或`/doc+`，編譯器會從可執行檔或程式庫編譯器建立的 XML 檔案名稱。 如果您使用`/doc-`或不指定`/doc`選項，編譯器不會建立 XML 檔案。  
  
 在原始程式檔中，文件註解可以在下列定義之前︰  
  
-   使用者定義型別，例如[類別](../../../visual-basic/language-reference/statements/class-statement.md)或[介面](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   成員，例如欄位、[事件](../../../visual-basic/language-reference/statements/event-statement.md)，[屬性](../../../visual-basic/language-reference/statements/property-statement.md)，[函式](../../../visual-basic/language-reference/statements/function-statement.md)，或[副程式](../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
 若要使用產生的 XML 檔案，與[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense)功能，可讓您想要支援的組件相同的 XML 檔案的檔案名稱。 請確定 XML 檔案是組件相同目錄中，讓組件中的參考時[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]專案中的.xml 檔案也找到。 XML 文件檔案不是要讓 IntelliSense 在專案或專案所參考之專案中的程式碼的運作必要的。  
  
 除非您使用編譯`/target:module`，XML 檔案包含標記`<assembly></assembly>`。 這些標記會指定包含編譯輸出檔的組件資訊清單的檔案名稱。  
  
 請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)的方式來產生文件從您的程式碼中的註解。  
  
|在 Visual Studio 中設定 /doc 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [編譯]**** 索引標籤。<br />3.在設定的值**產生 XML 文件檔案**方塊。|  
  
## <a name="example"></a>範例  
 請參閱[記載您的程式碼使用 XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)範例。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
