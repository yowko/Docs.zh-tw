---
title: 這是固定陣列，或陣列暫被鎖定
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350780"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>此陣列為固定長度或暫時鎖定 (Visual Basic)
此錯誤的可能原因如下：  
  
- 使用 `ReDim` 變更固定大小陣列的元素數目。  
  
- Redimensioning 模組層級動態陣列，其中一個元素已當做引數傳遞至程式。 如果傳遞了元素，陣列就會鎖定，以避免在程式內解除配置參考參數的記憶體。  
  
- 嘗試將值指派給包含陣列的 `Variant` 變數，但 `Variant` 目前已鎖定。  
  
## <a name="to-correct-this-error"></a>若要改正這項錯誤  
  
1. 將原始陣列設為動態，而不是修正，方法是使用 `ReDim` （如果陣列是在程式內宣告），或是宣告它而不指定專案數（如果陣列是在模組層級宣告）。  
  
2. 判斷您是否真的需要傳遞專案，因為它在模組的所有程式中都是可見的。  
  
3. 判斷哪些鎖定 `Variant` 並加以修正。  
  
## <a name="see-also"></a>另請參閱

- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
