---
title: -recurse
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 195d4b8f8e88d22e63c29ab9152399eb5c4a19df
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="-recurse"></a>-recurse
編譯指定的目錄或專案目錄的子目錄中的原始程式檔。  
  
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
 您也可以在檔案名稱中使用萬用字元，編譯專案目錄中所有相符的檔案，而不使用`-recurse`。 如果沒有任何輸出檔案名稱指定時，編譯器會根據處理第一個輸入檔的輸出檔案名稱。 這通常是在編譯時依字母順序檢視檔清單中的第一個檔案。 基於這個理由，建議您最好以指定輸出檔案使用`-out`選項。  
  
> [!NOTE]
>  `-recurse`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列命令會編譯目前的目錄中的所有 Visual Basic 檔案。  
  
```console
vbc *.vb  
```  
  
 下列命令會編譯中的所有 Visual Basic 檔案`Test\ABC`目錄和任何目錄下方，然後產生`Test.ABC.dll`。  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
