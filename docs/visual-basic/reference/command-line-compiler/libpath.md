---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: dff7e0c3eb696b9b18f4c4e59240a26c1cb9782c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408545"
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
|`dirList`|必要。 以分號分隔的目錄清單，如果在目前的工作目錄（您叫用編譯器的目錄）或 common language runtime 的系統目錄中找不到參考的元件，則為要查看的目錄。 如果目錄名稱包含空格，請將名稱括在引號（""）中。|  
  
## <a name="remarks"></a>備註  
 `-libpath`選項會指定[-reference](reference.md)選項所參考之元件的位置。  
  
 編譯器會以下列順序搜尋不完整的組件參考：  
  
1. 目前的工作目錄。 這是叫用編譯器的起點目錄。  
  
2. 通用語言執行平台系統目錄。  
  
3. 所指定的目錄 `-libpath` 。  
  
4. LIB 環境變數所指定的目錄。  
  
 此 `-libpath` 選項為加法; 指定超過一次會附加至任何先前的值。  
  
 使用 `-reference` 來指定元件參考。  
  
|在 Visual Studio 的整合式開發環境中設定-libpath|  
|---|  
|1. 在**方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。 <br />2. 按一下 [**參考**] 索引標籤。<br />3. 按一下 [**參考路徑 ...** ] 按鈕。<br />4. 在 [**參考路徑**] 對話方塊的 [**資料夾：** ] 方塊中，輸入目錄名稱。<br />5. 按一下 [**新增資料夾**]。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `T2.vb` 以建立 .exe 檔案。 編譯器會查看工作目錄、C：磁片磁碟機的根目錄，以及 C：磁片磁碟機的新元件目錄中的元件參考。  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../../standard/assembly/index.md)
- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
