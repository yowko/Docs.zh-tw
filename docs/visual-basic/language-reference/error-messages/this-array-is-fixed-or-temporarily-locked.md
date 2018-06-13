---
title: 此陣列為固定長度或暫時鎖定 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: e912bd202603d9a0f427418708ad584c7d6203e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593560"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>此陣列為固定長度或暫時鎖定 (Visual Basic)
此錯誤有下列可能原因：  
  
-   使用`ReDim`可以變更的固定大小陣列的項目數目。  
  
-   Redimensioning 模組層級動態陣列，在其中一個項目已傳遞做為引數至程序。 如果傳遞的項目，陣列會鎖定以防止解除配置記憶體的程序內參考參數。  
  
-   嘗試指派值給`Variant`變數，其中包含屬於陣列、 但`Variant`目前已鎖定。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請原始陣列，而不是藉由宣告它具有固定動態`ReDim`（如果陣列宣告程序內），或藉由宣告但未指定的項目數 （如果在模組層級中宣告陣列。  
  
2.  決定您是否真的需要將項目，因為它是在模組中的所有程序內為可見。  
  
3.  判斷哪些鎖定`Variant`及修復它。  
  
## <a name="see-also"></a>另請參閱  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
