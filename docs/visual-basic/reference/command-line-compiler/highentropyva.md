---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 4d88c302281097fabd0eb361d60319bc8a0daf8d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058062"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic) 

指出64位可執行檔或由 [-platform： anycpu](platform.md) 編譯器選項標記的可執行檔，是否支援高熵位址空間配置隨機載入 (ASLR) 。  
  
## <a name="syntax"></a>語法  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>引數  

 `+` &#124; `-`  
 選擇性。 此選項預設為關閉，或指定 `-highentropyva-` 。 如果您指定或，就會開啟此選項 `-highentropyva` `-highentropyva+` 。  
  
## <a name="remarks"></a>備註  

 如果您指定此選項，當核心隨機化進程的位址空間配置作為 ASLR 的一部分時，相容的 Windows 核心版本可能會使用較高程度的熵。 如果核心使用較高程度的熵，可將較大量的位址配置給記憶體區域（例如堆疊和堆積）。 因此更難猜測特定記憶體區域的位置。  
  
 當此選項為 on 時，目標可執行檔及其相依的任何模組，都必須能夠處理大於 4 gb (GB 的指標值，) 當這些模組以64位進程的形式執行時。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
