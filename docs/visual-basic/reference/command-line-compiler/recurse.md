---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 4281c7bf5a7972d323e1e649aaef437c7ee901ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956269"
---
# <a name="-recurse"></a>-recurse
編譯指定目錄或專案目錄之所有子目錄中的原始程式碼檔。  
  
## <a name="syntax"></a>語法  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引數  
 `dir`  
 選擇性。 您想要開始搜尋的目錄。 如果未指定, 則搜尋會從專案目錄開始。  
  
 `file`  
 必要項。 要搜尋的檔案。 允許萬用字元。  
  
## <a name="remarks"></a>備註  
 您可以在檔案名中使用萬用字元, 來編譯專案目錄中的所有相符檔案, 而`-recurse`不使用。 如果未指定輸出檔名稱, 編譯器會在第一個處理的輸入檔案上以輸出檔案名為基礎。 這通常是在按字母順序查看時所編譯的檔案清單中的第一個檔案。 基於這個理由, 最好是使用`-out`選項來指定輸出檔。  
  
> [!NOTE]
> 此`-recurse`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。  
  
## <a name="example"></a>範例  
 下列命令會編譯目前目錄中的所有 Visual Basic 檔案。  
  
```console
vbc *.vb  
```  
  
 下列命令會編譯目錄中的所有 Visual Basic `Test\ABC`檔案和其底下的任何目錄, 然後產生`Test.ABC.dll`。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
