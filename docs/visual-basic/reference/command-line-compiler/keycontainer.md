---
title: "/keycontainer |Microsoft 文件"
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
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 68fa09edce5c0c9af143197f9379d5a46afab52e
ms.lasthandoff: 03/13/2017

---
# <a name="keycontainer"></a>/keycontainer
指定金鑰組的金鑰容器名稱，為組件提供強式名稱。  
  
## <a name="syntax"></a>語法  
  
```  
/keycontainer:container  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`container`|必要項。 包含金鑰的容器檔案。 將檔案名稱括在引號 ("") 如果名稱包含空格。|  
  
## <a name="remarks"></a>備註  
 藉由將公開金鑰插入組件資訊清單，以及使用私密金鑰簽署最終組件，編譯器會建立可共用的元件。 若要產生金鑰檔，請輸入`sn -k``file`在命令列。 `-i`選項會將金鑰組安裝至容器。 如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。  
  
 如果您使用編譯`/target:module`，金鑰檔的名稱是保留在模組中，併入編譯的組件時，會建立組件[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。  
  
 您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute>) 中的任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼。</xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 您也可以將加密資訊給編譯器以[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)。 使用[/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)如果您想要的部分簽署組件。  
  
 請參閱[建立和使用強式名稱組件](https://msdn.microsoft.com/library/xwb8f617)如需有關簽署組件。  
  
> [!NOTE]
>  `/keycontainer`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯原始程式檔`Input.vb`和指定的金鑰容器。  
  
```  
vbc /keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
