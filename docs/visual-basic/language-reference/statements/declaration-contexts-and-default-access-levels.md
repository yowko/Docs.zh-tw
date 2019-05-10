---
title: 宣告內容和預設存取層級 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 05c2d6420526b660ead2f50eba7feb6b20524705
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623934"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>宣告內容和預設存取層級 (Visual Basic)
本主題說明哪一個 Visual Basic 類型可以宣告內的其他類型，以及什麼其存取層級預設為如果未指定。  
  
## <a name="declaration-context-levels"></a>宣告內容層級  
 *宣告內容*的程式設計項目會宣告它的程式碼區域。 這通常是另一個的程式設計元素，然後呼叫*包含項目的*。  
  
 宣告內容的等級如下所示：  
  
- *命名空間層級*— 在原始程式檔或命名空間內，但不是會在類別、 結構、 模組或介面  
  
- *模組層級*— 類別、 結構、 模組或介面內，但不是會在程序或區塊  
  
- *程序層級*— 程序或區塊內 (例如`If`或`For`)  
  
 下表顯示各種宣告的程式設計元素，其宣告內容根據的預設存取層級。  
  
|宣告項目|命名空間層級|模組層級|程序層級|  
|----------------------|---------------------|------------------|---------------------|  
|變數 ([Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md))|不允許|`Private` (`Public`中`Structure`，不允許在`Interface`)|`Public`|  
|常數 ([Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md))|不允許|`Private` (`Public`中`Structure`，不允許在`Interface`)|`Public`|  
|列舉型別 ([Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|不允許|  
|類別 ([Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|不允許|  
|結構 ([結構，陳述式](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|不允許|  
|模組 ([Module 陳述式](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|不允許|不允許|  
|介面 ([Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|不允許|  
|程序 ([Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)， [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md))|不允許|`Public`|不允許|  
|外部參考 ([Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md))|不允許|`Public` (不允許在`Interface`)|不允許|  
|運算子 ([Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md))|不允許|`Public` (在中不允許`Interface`或`Module`)|不允許|  
|屬性 ([Property Statement](../../../visual-basic/language-reference/statements/property-statement.md))|不允許|`Public`|不允許|  
|預設屬性 ([預設](../../../visual-basic/language-reference/modifiers/default.md))|不允許|`Public` (不允許在`Module`)|不允許|  
|事件 ([Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md))|不允許|`Public`|不允許|  
|委派 ([Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|不允許|  
  
 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="see-also"></a>另請參閱

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
