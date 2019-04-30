---
title: 此陣列為固定長度或暫時鎖定 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c74d9524ff64101ba6002e133b93c9b80e8f50a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982445"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>此陣列為固定長度或暫時鎖定 (Visual Basic)
此錯誤有下列可能的原因：  
  
- 使用`ReDim`若要變更的固定大小陣列的項目數。  
  
- Redimensioning 模組層級動態陣列，在其中一個項目已傳遞做為引數給程序。 如果傳遞的項目，則陣列會鎖定以防止解除配置記憶體的程序內參考參數。  
  
- 嘗試指派值給`Variant`變數，其中包含陣列，但`Variant`目前已鎖定。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 將原始陣列設為動態，而不是藉由宣告它與已修正`ReDim`（如果陣列宣告程序內），或藉由宣告但未指定的元素數目 （如果陣列在模組層級中宣告。  
  
2. 判斷您是否真的需要將項目，因為它是在模組中的所有程序內為可見。  
  
3. 判斷功能正鎖住`Variant`並加以修正它。  
  
## <a name="see-also"></a>另請參閱

- [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
