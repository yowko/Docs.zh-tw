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
ms.openlocfilehash: 726f3dd179aedb39b578c8580c9632182af2d5e0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085122"
---
# <a name="-resource-visual-basic"></a>-resource (Visual Basic) 

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
|`filename`|必要。 要內嵌在輸出檔中的資源檔名稱。 依預設，在 `filename` 元件中是公用的。 以引號括住檔案名 ( "" ) 如果它包含空格。|  
|`identifier`|選擇性。 資源的邏輯名稱;用來載入它的名稱。 預設值是檔案的名稱。 您可以選擇性地在組件資訊清單中指定資源為公用或私用，如下所示： `-res:filename.res, myname.res, public`|  
  
## <a name="remarks"></a>備註  

 用 `-linkresource` 來將資源連結至元件，而不將資源檔放在輸出檔中。  
  
 例如，如果 `filename` 是 .NET Framework 資源檔（例如 [Resgen.exe (資源檔 ](../../../framework/tools/resgen-exe-resource-file-generator.md) 產生器) 或開發環境中所建立），則可以使用命名空間中的成員進行存取 (如需 <xref:System.Resources> 詳細資訊，請參閱 <xref:System.Resources.ResourceManager>) 。 若要在執行時間存取所有其他資源，請使用下列其中一種方法： <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A> 、 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 或 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 。  
  
 `-resource` 的簡短形式為 `-res`。  
  
 如需如何 `-resource` 在 VISUAL STUDIO IDE 中設定的詳細資訊，請參閱 [ ( .Net) 管理應用程式資源 ](/visualstudio/ide/managing-application-resources-dotnet)。  
  
## <a name="example"></a>範例  

 下列程式碼會編譯 `In.vb` 和附加資源檔 `Rf.resource` 。  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-win32resource](win32resource.md)
- [-linkresource (Visual Basic) ](linkresource.md)
- [-目標 (Visual Basic) ](target.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
