---
title: "/keyfile |Microsoft 文件"
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
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
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
ms.openlocfilehash: c36eac96ac6302db0b567e8249af726c807c2c6c
ms.lasthandoff: 03/13/2017

---
# <a name="keyfile"></a>/keyfile
指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。  
  
## <a name="syntax"></a>語法  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 必要項。 包含金鑰的檔案。 如果檔案名稱包含空格，將名稱括在引號 ("")。  
  
## <a name="remarks"></a>備註  
 編譯器會將公開金鑰插入組件資訊清單，然後使用私密金鑰簽署最終組件。 若要產生金鑰檔，請輸入`sn -k file`在命令列。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。  
  
 如果您使用編譯`/target:module`，金鑰檔的名稱是保留在模組中，併入編譯的組件時，會建立組件[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。  
  
 您也可以將加密資訊給編譯器以[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。 使用[/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)如果您想要的部分簽署組件。  
  
 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) 中任何 Microsoft 中繼語言模組的原始程式碼。</xref:System.Reflection.AssemblyKeyFileAttribute>  
  
 在案例中，同時`/keyfile`和[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) （命令列選項或是自訂屬性） 中指定相同的編譯，編譯器會先嘗試金鑰容器。 如果成功，組件已簽署金鑰容器中的資訊。 如果編譯器找不到金鑰容器，則會嘗試使用指定的檔案`/keyfile`。 如果這個動作成功、 簽署組件金鑰檔案中的資訊以及金鑰的資訊安裝在金鑰容器 (類似於`sn -i`)，以便在下次編譯時，金鑰容器才有效。  
  
 請注意，金鑰檔可能包含公用的金鑰。  
  
 請參閱[建立和使用強式名稱組件](https://msdn.microsoft.com/library/xwb8f617)如需有關簽署組件。  
  
> [!NOTE]
>  `/keyfile`選項不可以從[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]開發環境，它才可使用從命令列進行編譯。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯原始程式檔`Input.vb`和指定的金鑰檔。  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
