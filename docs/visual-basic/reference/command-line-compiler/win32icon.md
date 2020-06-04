---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 52ef0b991554c800dba4320b0c64c81ddd1b0ff4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414281"
---
# <a name="-win32icon"></a>-win32icon
在輸出檔中插入 .ico 檔案。 這個 .ico 檔案代表檔案**瀏覽器**中的輸出檔案。  
  
## <a name="syntax"></a>語法  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|要加入至輸出檔的 .ico 檔案。 將檔案名括在引號（""）中（如果它包含空格）。|  
  
## <a name="remarks"></a>備註  
 您可以使用 Microsoft Windows 資源編譯器（RC）來建立 .ico 檔案。 當您編譯 Visual C++ 程式時，會叫用資源編譯器;會從 .rc 檔案建立 .ico 檔案。 `-win32icon` 和 `-win32resource` 選項互斥。  
  
 請參閱[-linkresource （Visual Basic）](linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](resource.md)來附加 .NET Framework 資源檔。 請參閱[-win32resource](win32resource.md)以匯入 .res 檔案。  
  
|若要在 Visual Studio IDE 中設定-win32icon|  
|---|  
|1. 在**方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。 <br />2. 按一下 [**應用程式**] 索引標籤。<br />3. 修改 [**圖示**] 方塊中的值。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb` 並附加 .ico 檔案 `Rf.ico` 。  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
