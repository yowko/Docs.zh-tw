---
title: 這是固定陣列，或陣列暫被鎖定
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 05fb8e2ef788920fd200d79a75eec3d7c252b123
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873592"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>此陣列為固定長度或暫時鎖定 (Visual Basic)

此錯誤有下列可能的原因：  
  
- 使用 `ReDim` 變更固定大小陣列的元素數目。  
  
- Redimensioning 模組層級動態陣列，其中一個元素已做為引數傳遞至程式。 如果傳遞元素，則會鎖定陣列，以防止在程式內解除配置參考參數的記憶體。  
  
- 嘗試將值指派給 `Variant` 包含陣列的變數，但 `Variant` 目前已鎖定。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 如果陣列是在程式) 內宣告，或在不指定專案數目的情況下宣告，則讓原始陣列變成動態，而不是 (固定的 `ReDim` （如果陣列是在模組層級宣告，則會將它宣告，而不需要指定專案數目 (）。  
  
2. 判斷您是否真的需要傳遞元素，因為它會顯示在課程模組中的所有程式內。  
  
3. 判斷鎖定的內容 `Variant` ，並加以補救。  
  
## <a name="see-also"></a>另請參閱

- [陣列](../../programming-guide/language-features/arrays/index.md)
