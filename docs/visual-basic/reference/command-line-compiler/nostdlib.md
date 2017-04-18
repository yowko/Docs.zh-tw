---
title: "/nostdlib (Visual Basic) |Microsoft 文件"
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
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 3bacd7d51d12ec6c48dc11ff4b83d842a9e78a30
ms.lasthandoff: 03/13/2017

---
# <a name="nostdlib-visual-basic"></a>/nostdlib (Visual Basic)
讓編譯器不會自動參考標準程式庫。  
  
## <a name="syntax"></a>語法  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a>備註  
 `/nostdlib`選項移除 System.dll 組件的自動參考，並防止編譯器讀取 Vbc.rsp 檔案。 Vbc.rsp 檔案 — 所在 Vbc.exe 檔案的相同目錄中，參考常用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。  
  
> [!NOTE]
>  永遠會參照 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。  
  
> [!NOTE]
>  `/nostdlib`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`而不需要參考標準程式庫。 您必須設定`_MYTYPE`字串 「 空白 」 移除的條件式編譯常數`My`物件。  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
