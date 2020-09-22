---
title: 宣告內容及預設存取層級
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: a659481b34b8b44f1f387b464d5d9656ed98ab3f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874959"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>宣告內容和預設存取層級 (Visual Basic)

本主題說明哪些 Visual Basic 類型可以在其他類型中宣告，以及其存取層級預設為（如果未指定）。  
  
## <a name="declaration-context-levels"></a>宣告內容層級  

 程式設計專案的宣告 *內容* 是其宣告所在的程式碼區域。 這通常是另一個程式設計專案，也就是 *包含元素*。  
  
 宣告內容的層級如下：  
  
- *命名空間層級* -在原始檔或命名空間內，但不在類別、結構、模組或介面內  
  
- *模組層級* ：類別、結構、模組或介面內，但不在程式或區塊內  
  
- 程式*層級*：程式或區塊內 (例如 `If` 或 `For`)   
  
 下表顯示各種宣告的程式設計專案的預設存取層級（視其宣告內容而定）。  
  
|宣告項目|命名空間層級|模組層級|程式層級|  
|----------------------|---------------------|------------------|---------------------|  
|變數 ([Dim 語句](dim-statement.md)) |不允許|`Private`中的 (`Public` `Structure` ，在) 中不允許 `Interface`|`Public`|  
|常數 ([Const 語句](const-statement.md)) |不允許|`Private`中的 (`Public` `Structure` ，在) 中不允許 `Interface`|`Public`|  
|列舉 ([Enum 語句](enum-statement.md)) |`Friend`|`Public`|不允許|  
|Class ([Class 語句](class-statement.md)) |`Friend`|`Public`|不允許|  
|結構 ([結構語句](structure-statement.md)) |`Friend`|`Public`|不允許|  
|Module ([Module 語句](module-statement.md)) |`Friend`|不允許|不允許|  
|介面 ([介面語句](interface-statement.md)) |`Friend`|`Public`|不允許|  
|Procedure ([函數語句](function-statement.md)， [Sub 語句](sub-statement.md)) |不允許|`Public`|不允許|  
|External reference ([Declare 語句](declare-statement.md)) |不允許|`Public`) 中不允許 (`Interface`|不允許|  
|Operator ([運算子語句](operator-statement.md)) |不允許|`Public``Interface`或) 中不允許 `Module` (|不允許|  
|屬性 ([屬性語句](property-statement.md)) |不允許|`Public`|不允許|  
|[預設屬性 (預設](../modifiers/default.md)) |不允許|`Public`) 中不允許 (`Module`|不允許|  
|事件 ([事件語句](event-statement.md)) |不允許|`Public`|不允許|  
|委派 ([委派語句](delegate-statement.md)) |`Friend`|`Public`|不允許|  
  
 如需詳細資訊，請參閱 [Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="see-also"></a>另請參閱

- [Friend](../modifiers/friend.md)
- [私人](../modifiers/private.md)
- [公用](../modifiers/public.md)
