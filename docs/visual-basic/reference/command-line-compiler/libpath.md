---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: a91bd74d0be4f1cb223091ee2527f9567b4ca5db
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058465"
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
|`dirList`|必要。 如果在目前的工作目錄中找不到參考的元件 (您用來叫用編譯器) 或 common language runtime 系統目錄中的目錄，則為編譯器要查看的目錄清單（以分號分隔）。 如果目錄名稱包含空格，請用引號括住名稱 ( "" ) 。|  
  
## <a name="remarks"></a>備註  

 `-libpath`選項會指定[參考](reference.md)選項所參考之元件的位置。  
  
 編譯器會以下列順序搜尋不完整的組件參考：  
  
1. 目前的工作目錄。 這是叫用編譯器的起點目錄。  
  
2. 通用語言執行平台系統目錄。  
  
3. 由指定的目錄 `-libpath` 。  
  
4. LIB 環境變數所指定的目錄。  
  
 此 `-libpath` 選項為加法; 指定超過一次之後，就會附加到任何先前的值。  
  
 使用 `-reference` 指定元件參考。  
  
|在 Visual Studio 整合式開發環境中設定-libpath|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。 <br />2. 按一下 [ **參考** ] 索引標籤。<br />3. 按一下 [ **參考路徑 ...** ] 按鈕。<br />4. 在 [ **參考路徑** ] 對話方塊中，于 [ **資料夾：** ] 方塊中輸入目錄名稱。<br />5. 按一下 [ **新增資料夾**]。|  
  
## <a name="example"></a>範例  

 下列程式碼會 `T2.vb` 進行編譯，以建立 .exe 檔。 編譯器會在 C：磁片磁碟機的根目錄中，以及 C：磁片磁碟機的新元件目錄中尋找元件參考的工作目錄。  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../../standard/assembly/index.md)
- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
