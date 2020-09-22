---
title: 檔案已經開啟
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874178"
---
# <a name="file-already-open"></a>檔案已經開啟

有時候必須先關閉檔案，才能 `FileOpen` 進行其他或其他操作。 可能導致本錯誤的原因包括：  
  
- 已針對已開啟的檔案執行連續輸出模式作業 `FileOpen`  
  
- 語句指的是開啟的檔案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請先關閉檔案，再執行語句。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
