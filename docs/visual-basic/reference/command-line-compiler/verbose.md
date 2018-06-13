---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f257fce67d8e348b69404411c12ded785cfd68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652125"
---
# <a name="-verbose"></a>-verbose
讓編譯器以產生詳細的狀態和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定`-verbose`等同於指定`-verbose+`，因而導致編譯器發出詳細訊息。 這個選項的預設值是`-verbose-`。  
  
## <a name="remarks"></a>備註  
 `-verbose`選項顯示編譯器所發出的錯誤總數的相關資訊，會報告正在載入哪些組件的模組，並顯示目前正在進行編譯的檔案。  
  
> [!NOTE]
>  `-verbose`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`和指示編譯器將會顯示詳細的狀態資訊。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
