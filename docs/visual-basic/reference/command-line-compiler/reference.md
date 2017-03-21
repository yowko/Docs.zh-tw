---
title: "/reference (Visual Basic) |Microsoft 文件"
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
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
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
ms.openlocfilehash: 12344dba82131d6be2c32127de287a6e9e3efa39
ms.lasthandoff: 03/13/2017

---
# <a name="reference-visual-basic"></a>/reference (Visual Basic)
會導致編譯器提供給您正在編譯的專案中指定的組件的型別資訊。  
  
## <a name="syntax"></a>語法  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`fileList`|必要項。 組件檔案名稱的逗號分隔清單。 如果檔案名稱包含空格，請用引號括住名稱。|  
  
## <a name="remarks"></a>備註  
 您匯入的檔案必須包含組件中繼資料。 只有公用型別是在組件外部可見的。 [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)選項從模組匯入中繼資料。  
  
 如果您參考的組件 （組件 A） 本身也參考另一個組件 (組件 B)，如果您需要參考 B 組件︰  
  
-   來自組件 A 的型別繼承自型別或實作介面從 b 組件  
  
-   欄位、 屬性、 事件或方法，從組件 B 的傳回型別或參數型別會叫用。  
  
 使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一或多個組件參考所在的目錄。  
  
 編譯器無法辨識的組件 （而非模組） 中的型別，它必須強制解析的型別。 一種執行這是定義型別的執行個體。 其他方式可解決在組件的編譯器型別名稱。 例如，如果您是從組件中的型別繼承，型別名稱就會知道編譯器。  
  
 參考常用 Vbc.rsp 回應檔[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件中，依預設會使用。 使用`/noconfig`若不想讓編譯器使用 Vbc.rsp。  
  
 簡短形式`/reference`是`/r`。  
  
## <a name="example"></a>範例  
 下列程式碼編譯來源檔案我`nput.vb`M 從參考組件`etad1.dll`和 M`etad2.dll`產生 O`ut.exe`。  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/ 未設定](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [公用](../../../visual-basic/language-reference/modifiers/public.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
