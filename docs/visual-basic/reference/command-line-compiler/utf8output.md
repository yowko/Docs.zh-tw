---
title: "/utf8output (Visual Basic) |Microsoft 文件"
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
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
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
ms.openlocfilehash: 89f41527703df781f32015f386bf87c1383d9769
ms.lasthandoff: 03/13/2017

---
# <a name="utf8output-visual-basic"></a>/utf8output (Visual Basic)
使用 UTF-8 編碼顯示編譯器輸出。  
  
## <a name="syntax"></a>語法  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇項。 此選項的預設值是`/utf8output-`，這表示編譯器輸出不會使用 utf-8 編碼方式。 指定`/utf8output`等同於指定`/utf8output+`。  
  
## <a name="remarks"></a>備註  
 在某些國際設定，編譯器輸出無法正確顯示在主控台中。 在這種情況下，使用`/utf8output`和編譯器輸出重新導向至檔案。  
  
> [!NOTE]
>  `/utf8output`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`，並指示編譯器顯示輸出使用 utf-8 編碼方式。  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
