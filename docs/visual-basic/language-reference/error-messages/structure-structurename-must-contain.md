---
title: 結構&#39; &lt;structurename&gt; &#39;必須包含至少一個執行個體成員變數或至少一個執行個體事件宣告未標記為&#39;自訂&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>結構&#39; &lt;structurename&gt; &#39;必須包含至少一個執行個體成員變數或至少一個執行個體事件宣告未標記為&#39;自訂&#39;
結構定義不包含任何非共用的變數或非共用的非自訂事件。  
  
 每個結構必須具有的變數或套用至每個特定執行個體 （共用） 而不是所有執行個體共同的事件 ([共用](../../../visual-basic/language-reference/modifiers/shared.md))。 非共用的常數、 屬性和程序不符合此需求。 此外，如果有非共用的變數，且只能有一個非共用的事件，該事件不可以是`Custom`事件。  
  
 **錯誤 ID:** BC30941  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   定義至少一個變數或不是事件`Shared`。 如果您定義只有一個事件，它必須是非自訂，以及非共用。  
  
## <a name="see-also"></a>另請參閱  
 [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [如何：宣告結構](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structure 陳述式](../../../visual-basic/language-reference/statements/structure-statement.md)
