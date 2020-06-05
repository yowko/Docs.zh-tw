---
title: 結構 '<structurename>' 至少必須包含一個執行個體成員變數，或者至少要有一個執行個體事件宣告未標記為 'Custom'
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 7b5bda7b1a2ae37eb509c736deae1652dc5e6ab0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374014"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>結構 '\<structurename>' 至少必須包含一個執行個體成員變數，或者至少要有一個執行個體事件宣告未標記為 'Custom'
結構定義不包含任何非共用的變數或非共用的 noncustom 事件。  
  
 每個結構都必須有一個變數或一個套用至每個特定實例（非共用）的事件，而不是所有實例（[共用](../modifiers/shared.md)）。 非共用的常數、屬性和程式無法滿足這項需求。 此外，如果沒有非共用變數，而且只有一個非共用事件，該事件就不能是 `Custom` 事件。  
  
 **錯誤識別碼：** BC30941  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 定義至少一個不是的變數或事件 `Shared` 。 如果您只定義一個事件，它必須是 noncustom 和非共用的。  
  
## <a name="see-also"></a>另請參閱

- [結構](../../programming-guide/language-features/data-types/structures.md)
- [作法：宣告結構](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure 陳述式](../statements/structure-statement.md)
