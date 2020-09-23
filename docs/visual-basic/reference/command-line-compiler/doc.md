---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 8b80629ce9b2cd62f10d9a53279b83ba41bc4ece
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097705"
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
|`+` &#124; `-`|選擇性。 指定 + 或只 `-doc` 會導致編譯器產生檔資訊，並將其放入 XML 檔案中。 指定 `-` 相當於不指定，因此不 `-doc` 會建立任何檔資訊。|  
|`file`|如果使用 `-doc:`，則為必要項。 指定輸出 XML 檔案，該檔案會填入編譯之原始程式碼檔案中的批註。 如果檔案名包含空格，請在名稱前後加上引號 ( "" ) 。|  
  
## <a name="remarks"></a>備註  

 `-doc`選項會控制編譯器是否產生包含檔批註的 XML 檔案。 如果您使用 `-doc:file` 語法，參數會 `file` 指定 XML 檔案的名稱。 如果您使用 `-doc` 或 `-doc+` ，則編譯器會從編譯器所建立的可執行檔或程式庫取得 XML 檔案名。 如果您使用 `-doc-` 或未指定 `-doc` 選項，則編譯器不會建立 XML 檔案。  
  
 在原始程式碼檔中，檔批註可以在下列定義之前：  
  
- 使用者定義類型，例如 [類別](../../language-reference/statements/class-statement.md) 或 [介面](../../language-reference/statements/interface-statement.md)  
  
- 成員，例如 field、 [event](../../language-reference/statements/event-statement.md)、 [property](../../language-reference/statements/property-statement.md)、 [function](../../language-reference/statements/function-statement.md)或 [副程式](../../language-reference/statements/sub-statement.md)。  
  
 若要使用產生的 XML 檔案搭配 Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) 功能，請讓 XML 檔案的檔案名與您想要支援的元件相同。 請確定 XML 檔案與元件位於相同的目錄中，如此一來，當 Visual Studio 專案中參考元件時，也會找到 .xml 檔案。 IntelliSense 無法針對專案內的程式碼，或專案所參考專案內的程式碼，使用 XML 檔檔案。  
  
 除非您使用進行編譯，否則 XML 檔案會 `-target:module` 包含標記 `<assembly></assembly>` 。 這些標記會指定包含編譯輸出檔案之組件資訊清單的檔案名。  
  
 如需從程式碼中的批註產生檔的方法，請參閱 [XML 註解標記](../../language-reference/xmldoc/index.md) 。  
  
|若要在 Visual Studio 整合式開發環境中設定-doc|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。 <br />2. 按一下 [ **編譯** ] 索引標籤。<br />3. 在 [ **產生 XML 檔** 檔案] 方塊中設定值。|  
  
## <a name="example"></a>範例  

 如需範例，請參閱 [使用 XML 記載您的程式碼](../../programming-guide/program-structure/documenting-your-code-with-xml.md) 。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [使用 XML 加入程式碼註解](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
