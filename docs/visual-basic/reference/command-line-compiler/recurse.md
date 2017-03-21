---
title: "/recurse |Microsoft 文件"
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
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
caps.latest.revision: 12
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
ms.openlocfilehash: fbf7d67c7f70345e62ddbb03c8626b688b5c593b
ms.lasthandoff: 03/13/2017

---
# <a name="recurse"></a>/recurse
編譯原始程式碼檔指定的目錄或專案目錄中的所有子目錄中。  
  
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
 您也可以在檔案名稱中使用萬用字元，編譯專案目錄中所有相符的檔案，而不需使用`/recurse`。 如果沒有指定輸出檔名是，編譯器來建立輸出檔名稱，第一個處理的輸入檔。 這通常是在編譯時依字母順序檢視檔案清單中的第一個檔案。 基於這個理由，最好指定輸出檔使用`/out`選項。  
  
> [!NOTE]
>  `/recurse`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼編譯所有[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]目前目錄中的檔案。  
  
```  
vbc *.vb  
```  
  
 下列程式碼編譯所有[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]檔案中`Test\ABC`目錄和其下，任何目錄，然後產生`Test.ABC.dll`。  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
