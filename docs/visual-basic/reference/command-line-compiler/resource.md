---
title: "/resource (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b46800322fd03eb2578cc558cc1d9bb78550aa61
ms.lasthandoff: 03/13/2017

---
# <a name="resource-visual-basic"></a>/resource (Visual Basic)
將 Managed 資源內嵌至組件中。  
  
## <a name="syntax"></a>語法  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`filename`|必要項。 資源檔嵌入至輸出檔的名稱。 根據預設，`filename`是公用的組件中。 將檔案名稱括在引號 ("") 如果它包含空格。|  
|`identifier`|選擇項。 資源; 的邏輯名稱用來載入它的名稱。 預設為檔案的名稱。 您可以選擇性地指定資源是否公用或私用組件資訊清單中，使用下列︰ `/res:``filename.res`，`myname.res`，`public`|  
  
## <a name="remarks"></a>備註  
 使用`/linkresource`資源連結到組件不需將資源檔放在輸出檔案。  
  
 如果`filename`是[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]建立資源檔，例如，由[Resgen.exe （資源檔產生器）](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)或在開發環境中，它可以存取與其中成員保持<xref:System.Resources>命名空間 (請參閱<xref:System.Resources.ResourceManager>如需詳細資訊)。</xref:System.Resources.ResourceManager> </xref:System.Resources> 若要在執行階段存取所有其他資源，請使用下列方法之一︰ <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>， <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>，或<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</xref:System.Reflection.Assembly.GetManifestResourceStream%2A> </xref:System.Reflection.Assembly.GetManifestResourceNames%2A> </xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>  
  
 簡短形式`/resource`是`/res`。  
  
 如需有關如何設定資訊`/resource`在 Visual Studio IDE 中，請參閱[管理應用程式資源 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`會附加至資源檔和`Rf.resource`。  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)   
 [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
