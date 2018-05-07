---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5044bc0093960fdf6b063450d8d3a57575ff07c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-libpath"></a>-libpath
指定的參考組件的位置。  
  
## <a name="syntax"></a>語法  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`dirList`|必要。 以分號分隔清單的編譯器，如果查詢參考的組件的目錄找不到在目前工作目錄 (directory 叫編譯器) 或 common language runtime 的系統目錄。 如果目錄名稱包含空格，將名稱括在引號 ("")。|  
  
## <a name="remarks"></a>備註  
 `-libpath`選項會指定所參考的組件位置[-參考](../../../visual-basic/reference/command-line-compiler/reference.md)選項。  
  
 編譯器會以下列順序搜尋不完整的組件參考：  
  
1.  目前的工作目錄。 這是叫用編譯器的起點目錄。  
  
2.  通用語言執行平台系統目錄。  
  
3.  所指定的目錄`/libpath`。  
  
4.  LIB 環境變數所指定的目錄。  
  
 `-libpath`選項是加總，則指定它超過一次將附加至任何先前的值。  
  
 使用`-reference`來指定組件參考。  
  
|在 Visual Studio 中設定 /libpath 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [參考] 節點。<br />3.按一下**參考路徑...**  按鈕。<br />4.在**參考路徑**對話方塊方塊中，輸入中的目錄名稱**資料夾：**方塊。<br />5.按一下**加入資料夾**。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`建立.exe 檔。 編譯器會尋找組件參考的工作目錄、 c： 磁碟機的根目錄和新的組件目錄中的 c： 磁碟機。  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
