---
title: "/linkresource (Visual Basic) |Microsoft 文件"
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
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fafde6563340189108a879b82e7e880aca690b39
ms.lasthandoff: 03/13/2017

---
# <a name="linkresource-visual-basic"></a>/linkresource (Visual Basic)
建立與 Managed 資源的連結。  
  
## <a name="syntax"></a>語法  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 必要項。 要連結至組件的資源檔。 如果檔案名稱包含空格，將名稱括在引號 ("")。  
  
 `identifier`  
 選擇項。 資源的邏輯名稱。 用來載入資源的名稱。 預設為檔案的名稱。 您可以選擇性地指定檔案是否公用或私用組件資訊清單中，例如︰ `/linkres:filename.res,myname.res,public`。 根據預設，`filename`是公用的組件中。  
  
## <a name="remarks"></a>備註  
 `/linkresource`選項不會在輸出檔案中內嵌資源檔，使用`/resource`選項來執行這項操作。  
  
 `/linkresource`選項需要其中`/target`以外的其他選項`/target:module`。  
  
 如果`filename`是[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]建立資源檔，例如，由[Resgen.exe （資源檔產生器）](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)或在開發環境中，它可以存取與其中成員保持<xref:System.Resources>命名空間。</xref:System.Resources> (如需詳細資訊，請參閱<xref:System.Resources.ResourceManager>。)</xref:System.Resources.ResourceManager>若要在執行階段存取所有其他資源，請使用 開頭的方法`GetManifestResource`中<xref:System.Reflection.Assembly>類別。</xref:System.Reflection.Assembly>  
  
 檔案名稱可以是任何檔案格式。 例如，您可能要產生的組件中，原生 DLL 部分，以便安裝到全域組件快取和從組件中的 managed 程式碼存取。  
  
 簡短形式`/linkresource`是`/linkres`。  
  
> [!NOTE]
>  `/linkresource`選項不可以從 Visual Studio 開發環境，可僅當您編譯從命令列。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`和連結的資源檔`Rf.resource`。  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
