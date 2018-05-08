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
ms.openlocfilehash: ab5593455546e65bdd760d9e60532031dc1f12a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|`filename`|必要。 要內嵌至輸出檔的資源檔名稱。 根據預設，`filename`是公用的組件中。 將檔案名稱括在引號 ("") 如果包含空格。|  
|`identifier`|選擇性。 邏輯名稱的資源;用來將其載入的名稱。 預設值是檔案的名稱。 您可以選擇性地指定的資源如同下列是公用或私用組件資訊清單中： `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>備註  
 使用`-linkresource`要將資源連結至組件，不需將資源檔放在輸出檔。  
  
 如果`filename`是[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]建立資源檔，例如，藉由[Resgen.exe （資源檔產生器）](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ，或是在開發環境中，它可以存取與其中成員保持<xref:System.Resources>命名空間 （請參閱<xref:System.Resources.ResourceManager>如需詳細資訊)。 若要在執行階段存取所有其他資源，請使用下列方法之一： <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>， <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>，或<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>。  
  
 `-resource` 的簡短形式為 `-res`。  
  
 如需有關如何設定資訊`-resource`在 Visual Studio IDE 中，請參閱[管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`和附加資源檔`Rf.resource`。  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
