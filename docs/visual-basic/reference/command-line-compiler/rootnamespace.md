---
title: "/rootnamespace |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
dev_langs:
- VB
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
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
ms.openlocfilehash: 7b261efeb829a6c0b035d7364c63074412a91c7f
ms.lasthandoff: 03/13/2017

---
# <a name="rootnamespace"></a>/rootnamespace
指定所有類型宣告的命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`namespace`|在括住目前專案的所有型別宣告的命名空間名稱。|  
  
## <a name="remarks"></a>備註  
 如果您使用 Visual Studio 可執行檔 (Devenv.exe) 來編譯所建立的專案在 Visual Studio 整合式的開發環境中，使用`/rootnamespace`指定的值<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>屬性。</xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> 請參閱[Devenv 命令列參數](https://docs.microsoft.com/visualstudio/ide/reference/devenv-command-line-switches)如需詳細資訊。  
  
 使用 common language runtime MSIL 反組譯工具 (我`ldasm.exe`) 來檢視輸出檔中的命名空間名稱。  
  
|在 Visual Studio 中設定 /rootnamespace 整合式開發環境|  
|---|  
|1.在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.按一下 [應用程式] **** 索引標籤。<br />3.修改中的值**根命名空間**方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`封入命名空間中的所有型別宣告和`mynamespace`。  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Ildasm.exe （IL 反組譯工具）](https://msdn.microsoft.com/library/f7dy01k1)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
