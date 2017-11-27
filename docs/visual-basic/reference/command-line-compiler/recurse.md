---
title: /recurse
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb69c7c44dcc2e8da5eb8a76f7d22f936a6d948f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="recurse"></a>/recurse
編譯指定的目錄或專案目錄的子目錄中的原始程式檔。  
  
## <a name="syntax"></a>語法  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a>引數  
 `dir`  
 選擇項。 您想要開始搜尋的目錄。 如果未指定，則會在專案目錄中開始搜尋。  
  
 `file`  
 必要項。 要搜尋的檔案。 允許萬用字元。  
  
## <a name="remarks"></a>備註  
 您也可以在檔案名稱中使用萬用字元，編譯專案目錄中所有相符的檔案，而不使用`/recurse`。 如果沒有任何輸出檔案名稱指定時，編譯器會根據處理第一個輸入檔的輸出檔案名稱。 這通常是在編譯時依字母順序檢視檔清單中的第一個檔案。 基於這個理由，建議您最好以指定輸出檔案使用`/out`選項。  
  
> [!NOTE]
>  `/recurse`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯所有[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]目前目錄中的檔案。  
  
```  
vbc *.vb  
```  
  
 下列程式碼會編譯所有[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]檔案`Test\ABC`目錄和任何目錄下方，然後產生`Test.ABC.dll`。  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
