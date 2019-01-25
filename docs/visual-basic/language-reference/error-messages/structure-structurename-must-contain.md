---
title: 結構&#39;&lt;結構名稱&gt;&#39;必須包含至少一個執行個體成員變數或至少一個執行個體事件宣告未標記為&#39;自訂&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: d8c654c212a459d40c6cf20cd62c3e0fcda8511b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603777"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>結構&#39;&lt;結構名稱&gt;&#39;必須包含至少一個執行個體成員變數或至少一個執行個體事件宣告未標記為&#39;自訂&#39;
結構的定義不包含任何非共用的變數或非共用的非自訂事件。  
  
 每個結構必須是變數或套用至每個特定執行個體 （非共用） 而不是所有執行個體共同的事件 ([共用](../../../visual-basic/language-reference/modifiers/shared.md))。 非共用的常數、 屬性和程序不符合此需求。 此外，如果有任何非共用的變數，只有一個非共用的事件，該事件不可以是`Custom`事件。  
  
 **錯誤 ID:** BC30941  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   定義至少一個變數或不是`Shared`。 如果您定義只有一個事件時，它必須是非自訂，以及非共用。  
  
## <a name="see-also"></a>另請參閱
- [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [如何：宣告結構](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
