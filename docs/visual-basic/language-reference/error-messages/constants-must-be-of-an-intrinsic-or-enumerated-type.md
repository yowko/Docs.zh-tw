---
title: 常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: a9bbf27615233f4282e481710a0234b2fa589f63
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874557"
---
# <a name="constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a>常數必須是內建或列舉類型，而不是類別、結構、型別參數或陣列類型

您已嘗試將常數宣告為類別、結構或陣列類型，或宣告為包含泛型型別所定義的型別參數。  
  
 常數必須是內建類型 (、、、、、、、、、、、、、 `Boolean` `Byte` `Date` `Decimal` `Double` `Integer` `Long` `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` 或 `UShort`) ，或是以 `Enum` 其中一個整數類型為基礎的型別。  
  
 **錯誤識別碼：** BC30424  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 將常數宣告為內建函式或 `Enum` 類型。  
  
2. 常數也可以是特殊值 `True` ，例如、 `False` 或 `Nothing` 。 編譯器會將這些預先定義的值視為適當的內建類型。  
  
## <a name="see-also"></a>另請參閱

- [常數和列舉](../constants-and-enumerations.md)
- [Data types (資料類型)](../../programming-guide/language-features/data-types/index.md)
- [Data types (資料類型)](../data-types/index.md)
