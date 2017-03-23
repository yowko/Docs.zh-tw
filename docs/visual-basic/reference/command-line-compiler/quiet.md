---
title: "/quiet |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
dev_langs:
- VB
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
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
ms.openlocfilehash: feafed7464248c38ec70087795a28ead8b8793f3
ms.lasthandoff: 03/13/2017

---
# <a name="quiet"></a>/quiet
防止編譯器顯示語法相關錯誤和警告的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
/quiet  
```  
  
## <a name="remarks"></a>備註  
 `/quiet` 預設為非作用中。 當編譯器報告與語法相關的錯誤或警告時，它也會輸出原始程式碼中的一行。 對於剖析編譯器輸出的應用程式，可能會更方便編譯器輸出的診斷文字。  
  
 在下列範例中，`Module1`輸出錯誤包含原始程式碼，而不需要編譯時`/quiet`。  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 輸出：  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 以編譯`/quiet`，編譯器只會輸出下列︰  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  `/quiet`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`並不會顯示與語法相關編譯器診斷程式碼︰  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
