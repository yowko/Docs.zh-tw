---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 8f4e415576562885c9edbd3d2dddbe2a271e9923
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005462"
---
# <a name="-libpath"></a>-libpath
指定參考元件的位置。  
  
## <a name="syntax"></a>語法  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`dirList`|必要項。 以分號分隔的目錄清單，如果在目前的工作目錄（您叫用編譯器的目錄）或 common language runtime 的系統目錄中找不到參考的元件，則為要查看的目錄。 如果目錄名稱包含空格，請將名稱括在引號（""）中。|  
  
## <a name="remarks"></a>備註  
 @No__t-0 選項會指定[-reference](../../../visual-basic/reference/command-line-compiler/reference.md)選項所參考之元件的位置。  
  
 編譯器會以下列順序搜尋不完整的組件參考：  
  
1. 目前的工作目錄。 這是叫用編譯器的起點目錄。  
  
2. 通用語言執行平台系統目錄。  
  
3. @No__t-0 指定的目錄。  
  
4. LIB 環境變數所指定的目錄。  
  
 @No__t-0 選項為加法;指定超過一次以上會附加到任何先前的值。  
  
 使用 `-reference` 來指定元件參考。  
  
|在 Visual Studio 的整合式開發環境中設定/libpath|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [參考] 節點。<br />3.按一下 [**參考路徑 ...** ] 按鈕。<br />4.在 [**參考路徑**] 對話方塊的 [**資料夾：** ] 方塊中，輸入目錄名稱。<br />5.按一下 [**新增資料夾**]。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `T2.vb`，以建立 .exe 檔案。 編譯器會查看工作目錄、C：磁片磁碟機的根目錄，以及 C：磁片磁碟機的新元件目錄中的元件參考。  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../../standard/assembly/index.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
