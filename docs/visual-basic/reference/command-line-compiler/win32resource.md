---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004957"
---
# <a name="-win32resource"></a>-win32resource
將 Win32 資源檔插入輸出檔中。  
  
## <a name="syntax"></a>語法  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 要新增至輸出檔的資源檔名稱。 將檔案名括在引號（""）中（如果它包含空格）。  
  
## <a name="remarks"></a>備註  
 您可以使用 Microsoft Windows 資源編譯器（RC）來建立 Win32 資源檔。  
  
 Win32 資源可以包含版本或點陣圖（圖示）資訊，協助您在 [檔案**瀏覽器**] 中識別您的應用程式。 如果您未指定 `-win32resource`，則編譯器會根據元件版本產生版本資訊。 @No__t-0 和 @no__t 1 選項互斥。  
  
 請參閱[-linkresource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/resource.md)來附加 .NET Framework 資源檔。  
  
> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb`，並將 Win32 資源檔附加 `Rf.res`：  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
