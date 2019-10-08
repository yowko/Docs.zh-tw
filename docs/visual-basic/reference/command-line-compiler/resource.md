---
title: -資源（Visual Basic）
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 5bedc346381f6de293933dce14a8c5c3044b246f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005200"
---
# <a name="-resource-visual-basic"></a>-資源（Visual Basic）
將 Managed 資源內嵌至組件中。  
  
## <a name="syntax"></a>語法  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

或  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|必要項。 要內嵌至輸出檔的資源檔名稱。 根據預設，在元件中，`filename` 是公用的。 將檔案名括在引號（""）中（如果它包含空格）。|  
|`identifier`|選擇性。 資源的邏輯名稱。用來載入它的名稱。 預設值是檔案的名稱。 （選擇性）您可以在組件資訊清單中指定資源是否為公用或私用，如下所示： `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>備註  
 使用 `-linkresource`，將資源連結至元件，而不將資源檔放在輸出檔中。  
  
 如果 `filename` 是由[resgen.exe （資源檔](../../../framework/tools/resgen-exe-resource-file-generator.md)產生器）或在開發環境中建立的 .NET Framework 資源檔，則可以使用 @no__t 2 命名空間中的成員進行存取（如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager>）。 若要在執行時間存取所有其他資源，請使用下列其中一種方法： <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>、<xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 或 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>。  
  
 `-resource` 的簡短形式為 `-res`。  
  
 如需如何在 Visual Studio IDE 中設定 `-resource` 的詳細資訊，請參閱[管理應用程式資源（.net）](/visualstudio/ide/managing-application-resources-dotnet)。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb`，並將資源檔附加 `Rf.resource`。  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
