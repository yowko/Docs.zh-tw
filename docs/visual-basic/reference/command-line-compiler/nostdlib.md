---
title: /nostdlib (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d76563a5b3d439495899e07ce2df59c0acd75e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nostdlib-visual-basic"></a>/nostdlib (Visual Basic)
可讓編譯器不會自動參考標準程式庫。  
  
## <a name="syntax"></a>語法  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a>備註  
 `/nostdlib`選項會自動參考之 System.dll 組件，並可防止編譯器讀取 Vbc.rsp 檔案進行。 Vbc.rsp 檔案 — 所在 Vbc.exe 檔案相同的目錄中，參考常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。  
  
> [!NOTE]
>  一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。  
  
> [!NOTE]
>  `/nostdlib`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`不需參考標準程式庫。 您必須設定`_MYTYPE`字串 「 空白 」 移除的條件式編譯常數`My`物件。  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
