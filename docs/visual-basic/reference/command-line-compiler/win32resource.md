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
ms.openlocfilehash: bcbc690690993a094bc5360d0c13bddebf8cd615
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414242"
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
  
 Win32 資源可以包含版本或點陣圖（圖示）資訊，協助您在 [檔案**瀏覽器**] 中識別您的應用程式。 如果您未指定 `-win32resource` ，編譯器會根據元件版本產生版本資訊。 `-win32resource` 和 `-win32icon` 選項互斥。  
  
 請參閱[-linkresource （Visual Basic）](linkresource.md)來參考 .NET Framework 資源檔，或使用[-resource （Visual Basic）](resource.md)來附加 .NET Framework 資源檔。  
  
> [!NOTE]
> 此 `-win32resource` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb` 並附加 Win32 資源檔 `Rf.res` ：  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
