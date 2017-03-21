---
title: "/libpath |Microsoft 文件"
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
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
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
ms.openlocfilehash: cc534e782cff34f0c4882f3da2af973fed69ff80
ms.lasthandoff: 03/13/2017

---
# <a name="libpath"></a>/libpath
指定參考的組件的位置。  
  
## <a name="syntax"></a>語法  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`dirList`|必要項。 分號分隔清單的目錄中尋找參考的組件編譯器找不到在目前工作目錄 （從您所叫用編譯器的目錄） 或 common language runtime 的系統目錄。 如果目錄名稱包含空格，將名稱括在引號 ("")。|  
  
## <a name="remarks"></a>備註  
 `/libpath`選項會指定所參考的組件的位置[/參考](../../../visual-basic/reference/command-line-compiler/reference.md)選項。  
  
 編譯器會搜尋以下列順序並未完整限定的組件參考︰  
  
1.  目前工作目錄。 這是從編譯器叫用的目錄。  
  
2.  通用語言執行階段系統目錄。  
  
3.  所指定的目錄`/libpath`。  
  
4.  LIB 環境變數所指定的目錄。  
  
 `/libpath`選項是加總; 指定它超過一次附加到任何先前的值。  
  
 使用`/reference`來指定組件參考。  
  
|在 Visual Studio 中設定 /libpath 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [**參考**] 索引標籤。<br />3.按一下 [**參考路徑...** ] 按鈕。<br />4.在**參考路徑** 對話方塊中，輸入中的目錄名稱**資料夾︰**方塊。<br />5.按一下 **新增資料夾**。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`建立的.exe 檔案。 編譯器會將工作目錄中，c︰ 磁碟機的根目錄和 c︰ 磁碟機的新組件目錄中尋找組件參考。  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
