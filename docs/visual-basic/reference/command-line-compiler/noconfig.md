---
title: "/noconfig |Microsoft 文件"
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
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
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
ms.openlocfilehash: 304d0e7fc787adb1d7776a2c047090ffc230fcc1
ms.lasthandoff: 03/13/2017

---
# <a name="noconfig"></a>/noconfig
指定的編譯器應該不會自動參考常用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件或匯入`System`和`Microsoft.VisualBasic`命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>備註  
 `/noconfig`選項會告知編譯器不要編譯 Vbc.rsp 檔案時，Vbc.exe 檔案的相同目錄中。 Vbc.rsp 檔案參考常用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。 編譯器隱含地參考 System.dll 組件，除非`/nostdlib`指定選項。 `/nostdlib`選項會告知編譯器不要使用 Vbc.rsp 編譯或自動參考 System.dll 組件。  
  
> [!NOTE]
>  永遠會參照 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。  
  
 您可以修改 Vbc.rsp 檔案，以指定應包含在每個 Vbc.exe 編譯的其他編譯器選項 (除非指定`/noconfig`選項)。 如需詳細資訊，請參閱 [@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)。  
  
 編譯器會處理傳遞至選項`vbc`最後一個命令。 因此，在命令列上的任何選項會覆寫 Vbc.rsp 檔案中的相同選項設定。  
  
> [!NOTE]
>  `/noconfig`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="see-also"></a>另請參閱  
 [/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)   
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [@ （指定回應檔）](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
