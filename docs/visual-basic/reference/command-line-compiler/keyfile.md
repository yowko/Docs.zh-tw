---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0be7d230f16750395aaceb3c94539546716b8fd
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="keyfile"></a>/keyfile
指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。  
  
## <a name="syntax"></a>語法  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 必要。 包含索引鍵的檔案。 如果檔案名稱包含空格，將名稱括在引號 ("")。  
  
## <a name="remarks"></a>備註  
 編譯器的公開金鑰插入組件資訊清單，然後使用私密金鑰簽署最終組件。 若要產生的金鑰檔案，請輸入`sn -k file`在命令列。 如需詳細資訊，請參閱 [Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 如果您使用編譯`/target:module`，金鑰檔的名稱是保留在模組中，而且併入編譯的組件時所建立的組件[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。  
  
 您也可以使用 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 將加密資訊傳遞給編譯器。 如需部分簽署的組件，請使用 [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) 的任何 Microsoft 中繼語言模組的原始程式碼中。  
  
 在案例同時`/keyfile`和[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)指定 （根據命令列選項或是自訂屬性） 在相同編譯中，編譯器會先嘗試使用金鑰容器。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。 如果編譯器找不到金鑰容器，則會嘗試使用指定的檔案`/keyfile`。 如果此作業執行成功、 簽署組件金鑰檔案中的資訊和金鑰資訊會安裝在金鑰容器 (類似於`sn -i`)，因此在下次編譯時，金鑰容器會有效。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 請參閱[Creating and using strong-named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。  
  
> [!NOTE]
>  `/keyfile`選項不是可從[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]開發環境中，只有在從命令列編譯時，它是可用。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯原始程式檔`Input.vb`，並指定金鑰檔案。  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>請參閱  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
