---
title: "/verbose |Microsoft 文件"
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
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: 11
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
ms.openlocfilehash: f6d8a8b914ccffff72128bbc907482816b95b8a0
ms.lasthandoff: 03/13/2017

---
# <a name="verbose"></a>/verbose
讓編譯器產生詳細的狀態和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇項。 指定`/verbose`等同於指定`/verbose+`，這會使編譯器發出詳細訊息。 此選項的預設值是`/verbose-`。  
  
## <a name="remarks"></a>備註  
 `/verbose`選項顯示編譯器所發出的錯誤總數的相關資訊、 報告哪些組件正在載入的模組，以及顯示目前正在進行編譯的檔案。  
  
> [!NOTE]
>  `/verbose`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`，並指示編譯器顯示詳細的狀態資訊。  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
