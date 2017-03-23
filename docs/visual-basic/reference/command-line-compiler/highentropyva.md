---
title: "/highentropyva (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
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
ms.openlocfilehash: 34987930b3afd6d95d12190172a5a5e512106f8a
ms.lasthandoff: 03/13/2017

---
# <a name="highentropyva-visual-basic"></a>/highentropyva (Visual Basic)
指出是否在 64 位元可執行檔或可執行檔標記的[/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)編譯器選項支援高熵位址空間配置隨機載入 (ASLR)。  
  
## <a name="syntax"></a>語法  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇項。 此選項預設為關閉，或如果您指定`/highentropyva-`。 此選項為開啟如果您指定`/highentropyva`或`/highentropyva+`。  
  
## <a name="remarks"></a>備註  
 如果您指定這個選項時，Windows 核心的相容版本可以使用較高程度的高熵核心隨機放置程序的位址空間配置個做為 ASLR 一部分時。 如果核心使用較高程度的高熵，大量位址可以配置到記憶體區域，例如堆疊和堆積。 因此更難猜測特定記憶體區域的位置。  
  
 在選項設為目標的可執行檔和任何模組上時它相依必須能夠處理這些模組會做為 64 位元處理序執行時，會大於 4 gb 的指標值。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
