---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: c3bff4e44ddee1c4dfb6ab366464ad54e991b595
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624283"
---
# <a name="-doc"></a>-doc
將文件註解處理成 XML 檔案。  
  
## <a name="syntax"></a>語法  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 指定 +，或簡稱`-doc`，可讓編譯器產生文件資訊，並將它放在 XML 檔案。 指定`-`相當於未指定`-doc`，導致建立沒有文件資訊。|  
|`file`|如果使用 `-doc:`，則為必要項。 指定輸出 XML 檔案，其中會填入從編譯的原始程式檔的註解。 如果檔案名稱包含空格，括住的名稱加上引號 ("")。|  
  
## <a name="remarks"></a>備註  
 `-doc`選項會控制是否編譯器會產生包含文件註解的 XML 檔案。 如果您使用`-doc:file`語法，`file`參數會指定 XML 檔案的名稱。 如果您使用`-doc`或`-doc+`，編譯器會從可執行檔或編譯器所建立的文件庫中取得 XML 檔案名稱。 如果您使用`-doc-`，或不指定`-doc`選項，編譯器不會建立 XML 檔案。  
  
 在原始程式檔中，文件註解可以在前面的下列定義：  
  
- 使用者定義型別，例如[類別](../../../visual-basic/language-reference/statements/class-statement.md)或[介面](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
- 成員，為欄位，例如[事件](../../../visual-basic/language-reference/statements/event-statement.md)，[屬性](../../../visual-basic/language-reference/statements/property-statement.md)，[函式](../../../visual-basic/language-reference/statements/function-statement.md)，或[副程式](../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
 若要使用 Visual Studio 中使用產生的 XML 檔案[IntelliSense](/visualstudio/ide/using-intellisense)功能，可讓您想要支援的組件相同的 XML 檔案的檔案名稱。 請確定 XML 檔案是組件相同目錄中，以便當 Visual Studio 專案中參考組件時，也發現的.xml 檔案。 XML 文件檔案就不需要針對適用於在單一專案或專案所參考的專案中的程式碼的 IntelliSense。  
  
 除非您使用編譯`/target:module`，XML 檔案包含標記`<assembly></assembly>`。 這些標記會指定包含輸出檔編譯的組件資訊清單檔案的名稱。  
  
 請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)的方式，從您的程式碼中的註解產生文件。  
  
|若要設定-文件，在 Visual Studio 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.在設定的值**產生的 XML 文件檔案** 方塊中。|  
  
## <a name="example"></a>範例  
 請參閱[記錄您的程式碼與 XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)如需相關範例。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
