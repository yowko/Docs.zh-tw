---
title: -資源 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a69d0e15f9094860c4c66f3fe0a195a0a609db9
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746480"
---
# <a name="-resource-visual-basic"></a>-資源 (Visual Basic)
將 Managed 資源內嵌至組件中。  
  
## <a name="syntax"></a>語法  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|必要。 資源檔嵌入輸出檔的名稱。 根據預設，`filename`是公用的組件中。 將檔案名稱括在引號 ("") 如果它包含空格。|  
|`identifier`|選擇性。 資源; 的邏輯名稱用來將其載入的名稱。 預設值是檔案的名稱。 （選擇性） 您可以指定資源是否公用或私用組件資訊清單中，如同下列： `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>備註  
 使用`-linkresource`將資源連結至組件，不需將資源檔放在輸出檔。  
  
 如果`filename`已[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]建立的資源檔，例如，藉由[Resgen.exe （資源檔產生器）](../../../framework/tools/resgen-exe-resource-file-generator.md)或在開發環境中，它可以存取使用中的成員<xref:System.Resources>命名空間 （請參閱<xref:System.Resources.ResourceManager>如需詳細資訊)。 若要在執行階段存取所有其他資源，請使用其中一種下列方法： <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>， <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>，或<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>。  
  
 `-resource` 的簡短形式為 `-res`。  
  
 如需如何設定的詳細資訊`-resource`在 Visual Studio IDE 中，請參閱[管理的應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯`In.vb`和附加的資源檔`Rf.resource`。  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
- [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
- [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
