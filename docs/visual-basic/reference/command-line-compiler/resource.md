---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348560"
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
|`filename`|必要。 要內嵌至輸出檔的資源檔名稱。 根據預設， `filename`在元件中是公用的。 將檔案名括在引號（""）中（如果它包含空格）。|  
|`identifier`|選擇性。 資源的邏輯名稱。用來載入它的名稱。 預設值是檔案的名稱。 （選擇性）您可以在組件資訊清單中指定資源是否為公用或私用，如下所示：`-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>備註  
 用`-linkresource`來將資源連結至元件，而不將資源檔放在輸出檔中。  
  
 例如`filename` ，如果是由[Resgen.exe （資源檔](../../../framework/tools/resgen-exe-resource-file-generator.md)產生器）或在開發環境中建立的 .NET Framework 資源檔，則可以使用命名空間中的<xref:System.Resources>成員進行存取（如需詳細資訊<xref:System.Resources.ResourceManager> ，請參閱）。 若要在執行時間存取所有其他資源，請使用下列其中一種<xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>方法<xref:System.Reflection.Assembly.GetManifestResourceNames%2A>：、 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>或。  
  
 `-resource` 的簡短形式為 `-res`。  
  
 如需如何在 Visual Studio IDE `-resource`中設定的詳細資訊，請參閱[管理應用程式資源（.net）](/visualstudio/ide/managing-application-resources-dotnet)。  
  
## <a name="example"></a>範例  
 下列程式碼會`In.vb`編譯並附加資源`Rf.resource`檔。  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [-linkresource （Visual Basic）](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
