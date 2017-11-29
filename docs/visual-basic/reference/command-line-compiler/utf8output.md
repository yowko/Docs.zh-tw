---
title: /utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23c7c308865a6b6afb07443a42090fff3d9e2efb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="utf8output-visual-basic"></a>/utf8output (Visual Basic)
使用 UTF-8 編碼顯示編譯器輸出。  
  
## <a name="syntax"></a>語法  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇項。 這個選項的預設值是`/utf8output-`，這表示編譯器輸出不會使用 utf-8 編碼方式。 指定`/utf8output`等同於指定`/utf8output+`。  
  
## <a name="remarks"></a>備註  
 在某些國際設定，在編譯器輸出無法正確顯示在主控台中。 在這種情況下，使用`/utf8output`和編譯器輸出重新導向至檔案。  
  
> [!NOTE]
>  `/utf8output`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`，並指示要顯示之編譯器輸出使用 utf-8 編碼方式。  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
