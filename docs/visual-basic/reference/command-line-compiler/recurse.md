---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 1edb648ec574c0052b7b8314f4ada710c8b0fe01
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183330"
---
# <a name="-recurse"></a>-recurse
編譯指定的目錄或專案目錄中的所有子目錄中的原始程式檔。  
  
## <a name="syntax"></a>語法  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引數  
 `dir`  
 選擇性。 您想要開始搜尋的目錄。 如果未指定，則會在專案目錄中開始搜尋。  
  
 `file`  
 必要。 要搜尋的檔案。 允許萬用字元。  
  
## <a name="remarks"></a>備註  
 您可以在 檔案名稱使用萬用字元，來編譯專案目錄中的所有相符檔案，而不需使用`-recurse`。 如果不指定任何輸出檔案名稱，編譯器會根據處理的第一個輸入檔案的輸出檔案名稱。 這通常是依字母順序檢視時所編譯檔的清單中的第一個檔案。 基於這個理由，最好是指定輸出檔案使用`-out`選項。  
  
> [!NOTE]
>  `-recurse`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="example"></a>範例  
 下列命令會編譯目前目錄中的所有 Visual Basic 檔案。  
  
```console
vbc *.vb  
```  
  
 下列命令會編譯中的所有 Visual Basic 檔案`Test\ABC`目錄和其下的任何目錄，然後產生`Test.ABC.dll`。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
