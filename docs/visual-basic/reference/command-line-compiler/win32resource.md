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
ms.openlocfilehash: d146f5967058b05795026cd7726ed5eda7ba3153
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91095404"
---
# <a name="-win32resource"></a>-win32resource

在輸出檔中插入 Win32 資源檔。  
  
## <a name="syntax"></a>語法  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a>引數  

 `filename`  
 要新增至輸出檔的資源檔名稱。 以引號括住檔案名 ( "" ) 如果它包含空格。  
  
## <a name="remarks"></a>備註  

 您可以使用 Microsoft Windows 資源編譯器 (RC) 來建立 Win32 資源檔。  
  
 Win32 資源可以包含版本或點陣圖 (圖示，) 可協助您在 **檔案總管**中識別應用程式的資訊。 如果您未指定 `-win32resource` ，編譯器會根據元件版本產生版本資訊。 `-win32resource` 和 `-win32icon` 選項互斥。  
  
 請參閱 [-linkresource (Visual Basic) ](linkresource.md) 來參考 .NET Framework 資源檔，或 [-資源 (Visual Basic ](resource.md)) ，以附加 .NET Framework 資源檔。  
  
> [!NOTE]
> `-win32resource`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  

 下列程式碼會編譯 `In.vb` 並附加 Win32 資源檔， `Rf.res` 如下所示：  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
