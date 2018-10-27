---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: d713a63c9503581f38048fe79c559883dc96efd2
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50040130"
---
# <a name="-libpath"></a>-libpath
指定參考的組件的位置。  
  
## <a name="syntax"></a>語法  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`dirList`|必要。 以分號分隔清單中的 改為查詢中參考的組件的目錄找不到在目前的工作目錄 （從中您叫用編譯器的目錄） 或 common language runtime 的系統目錄。 如果目錄名稱包含空格，將名稱括在引號 ("")。|  
  
## <a name="remarks"></a>備註  
 `-libpath`選項會指定所參考的組件的位置[-參考](../../../visual-basic/reference/command-line-compiler/reference.md)選項。  
  
 編譯器會以下列順序搜尋不完整的組件參考：  
  
1.  目前的工作目錄。 這是叫用編譯器的起點目錄。  
  
2.  通用語言執行平台系統目錄。  
  
3.  所指定的目錄`/libpath`。  
  
4.  LIB 環境變數所指定的目錄。  
  
 `-libpath`選項為加法; 指定超過一次附加到任何先前的值。  
  
 使用`-reference`來指定組件參考。  
  
|若要在 Visual Studio 中設定 /libpath 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [參考] 節點。<br />3.按一下 [**參考路徑...** ] 按鈕。<br />4.在 [**參考路徑**對話方塊方塊中，輸入中的目錄名稱**資料夾：** ] 方塊中。<br />5.按一下 **將資料夾新增**。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`來建立.exe 檔案。 編譯器會將工作目錄中的 c： 磁碟機的根目錄中，c： 磁碟機的新組件目錄中尋找的組件參考。  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
