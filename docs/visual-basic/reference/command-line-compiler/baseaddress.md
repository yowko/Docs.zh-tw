---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be88bf4834ca58b1fe708eb1ef7188c583fef0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress"></a>/baseaddress
建立 DLL 時，請指定預設基底地址。  
  
## <a name="syntax"></a>語法  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`address`|必要項。 DLL 的基底位址。 此位址必須指定為十六進位數字。|  
  
## <a name="remarks"></a>備註  
 DLL 預設基底地址由設定[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。  
  
 請注意這個位址的低序位字會捨入。 例如，如果您指定的是 0x11110001，它會捨入到 0x11110000。  
  
 若要完成 DLL 的簽章的程序，使用`–R`強式命名的工具 (Sn.exe) 選項。  
  
 如果目標不是 DLL，就會忽略此選項。  
  
|在 Visual Studio IDE 中設定 /baseaddress|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階**]。<br />4.修改中的值**DLL 基底位址：**方塊。 **注意：** **DLL 基底位址：**方塊是唯讀的除非目標是 DLL。|  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)
