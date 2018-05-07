---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
指出是否在 64 位元可執行檔或可執行檔標記的[/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)編譯器選項支援高熵位址空間配置隨機載入 (ASLR)。  
  
## <a name="syntax"></a>語法  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 此選項預設為 off，或如果您指定`-highentropyva-`。 選項為開啟如果您指定`-highentropyva`或`-highentropyva+`。  
  
## <a name="remarks"></a>備註  
 如果您指定這個選項，因為相容版本的 Windows 核心核心隨機放置程序的位址空間配置個做為 ASLR 一部分時可以使用較高程度的高熵。 如果核心使用的 entropy 較高程度，更大量的位址可以配置到記憶體區域，例如堆疊和堆積。 因此更難猜測特定記憶體區域的位置。  
  
 選項時，目標可執行檔和任何模組上的相依必須能夠處理這些模組做為 64 位元處理序執行時，不大於 4 gb 的指標值。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
