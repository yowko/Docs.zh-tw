---
title: "/win32icon |Microsoft 文件"
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
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
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
ms.openlocfilehash: 110a3861d6628dc2c3fb251aaa31762fb94f04c9
ms.lasthandoff: 03/13/2017

---
# <a name="win32icon"></a>/win32icon
將.ico 檔案插入至輸出檔。 這個.ico 檔案表示中的輸出檔**檔案總管**。  
  
## <a name="syntax"></a>語法  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|要加入至輸出檔的.ico 檔案。 將檔案名稱括在引號 ("") 如果它包含空格。|  
  
## <a name="remarks"></a>備註  
 您可以建立.ico 檔與 Microsoft Windows 資源編譯器 (RC)。 資源編譯器會叫用，當您編譯 Visual c + + 程式。.ico 檔案是從.rc 檔案建立。 `/win32icon`和`/win32resource`選項互斥。  
  
 請參閱[/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)參考[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]資源檔或[/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)附加[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]資源檔。 請參閱[/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .res 檔案匯入。  
  
|在 Visual Studio IDE 中設定 /win32icon|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [應用程式] **** 索引標籤。<br />3.修改中的值**圖示**方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`並附加.ico 檔， `Rf.ico`。  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
