---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 3da049b912d791f26814bb4b6cbb70998803726a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005643"
---
# <a name="-doc"></a>-doc
將文件註解處理成 XML 檔案。  
  
## <a name="syntax"></a>語法  
  
```console  
-doc[+ | -]  
```

或  

```console
-doc:file  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 指定 +，或只是 `-doc`，會使編譯器產生檔資訊，並將它放在 XML 檔案中。 指定 `-` 等同于不指定 `-doc`，因而不會建立任何檔資訊。|  
|`file`|如果使用 `-doc:`，則為必要項。 指定輸出 XML 檔案，其中會填入編譯的原始程式碼檔案中的批註。 如果檔案名包含空格，請使用引號（""）來括住名稱。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 選項可控制編譯器是否產生包含檔批註的 XML 檔案。 如果您使用 `-doc:file` 語法，則 `file` 參數會指定 XML 檔的名稱。 如果您使用 `-doc` 或 `-doc+`，編譯器會從編譯器所建立的可執行檔或程式庫取得 XML 檔案名。 如果您使用 `-doc-`，或未指定 `-doc` 選項，則編譯器不會建立 XML 檔案。  
  
 在原始程式碼檔中，檔批註可以在下列定義之前：  
  
- 使用者定義類型，例如[類別](../../../visual-basic/language-reference/statements/class-statement.md)或[介面](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
- 成員，例如欄位、[事件](../../../visual-basic/language-reference/statements/event-statement.md)、[屬性](../../../visual-basic/language-reference/statements/property-statement.md)、[函數](../../../visual-basic/language-reference/statements/function-statement.md)或[副程式](../../../visual-basic/language-reference/statements/sub-statement.md)。  
  
 若要使用產生的 XML 檔案搭配 Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense)功能，請讓 xml 檔案的檔案名與您要支援的元件相同。 請確定 XML 檔案與元件位於相同的目錄中，如此一來，當元件在 Visual Studio 專案中被參考時，也會找到 .xml 檔案。 IntelliSense 在專案內或專案所參考的專案內的程式碼都不需要使用 XML 檔檔案。  
  
 除非您使用 `/target:module` 進行編譯，否則 XML 檔案會包含標記 `<assembly></assembly>`。 這些標記會指定包含編譯輸出檔的組件資訊清單的檔案名。  
  
 如需從程式碼中的批註產生檔的方式，請參閱[XML 註解標記](../../../visual-basic/language-reference/xmldoc/index.md)。  
  
|若要在 Visual Studio 的整合式開發環境中設定-doc|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.在 [**產生 XML 檔**檔] 方塊中設定值。|  
  
## <a name="example"></a>範例  
 如需範例，請參閱[使用 XML 記載您的程式碼](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
