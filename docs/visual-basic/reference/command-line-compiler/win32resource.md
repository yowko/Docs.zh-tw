---
title: /win32resource
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d839b1100b1ae76fbd4653ebc60c79db11b77685
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="win32resource"></a>/win32resource
將 Win32 資源檔插入輸出檔中。  
  
## <a name="syntax"></a>語法  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 要加入至輸出檔的資源檔名稱。 將檔案名稱括在引號 ("") 如果包含空格。  
  
## <a name="remarks"></a>備註  
 您可以建立 Win32 資源檔與 Microsoft Windows 資源編譯器 (RC)。  
  
 Win32 資源可以包含版本或點陣圖 （圖示） 資訊可協助您識別應用程式中的**檔案總管**。 如果您未指定`/win32resource`，編譯器會產生組件版本為基礎的版本資訊。 `/win32resource`和`/win32icon`選項互斥。  
  
 請參閱[/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)參考[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]資源檔或[/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]資源檔。  
  
> [!NOTE]
>  `/win32resource`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`，並將 Win32 資源檔，附加`Rf.res`:  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
