---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 6b4b69d227c857442de6857fac023090b3698e81
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004640"
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
 您可以使用 Microsoft Windows 資源編譯器（RC）來建立 .ico 檔案。 當您編譯視覺效果C++程式時，會叫用資源編譯器;會從 .rc 檔案建立 .ico 檔案。 @No__t-0 和 @no__t 1 選項互斥。  
  
 請參閱[-linkresource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/resource.md)來附加 .NET Framework 資源檔。 請參閱[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)以匯入 .res 檔案。  
  
|若要在 Visual Studio IDE 中設定-win32icon|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [應用程式] 索引標籤。<br />3.修改 [**圖示**] 方塊中的值。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb`，並將 .ico 檔案附加 `Rf.ico`。  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
