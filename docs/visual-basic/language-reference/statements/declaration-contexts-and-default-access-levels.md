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
ms.openlocfilehash: b5bb943a062ac648f88645fb6de1acb42213071c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404793"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>宣告內容和預設存取層級 (Visual Basic)
本主題描述哪些 Visual Basic 類型可以在哪些其他類型中宣告，以及其存取層級預設為（如果未指定）。  
  
## <a name="declaration-context-levels"></a>宣告內容層級  
 程式設計專案的宣告*內容*是宣告它之程式碼的區域。 這通常是另一個程式設計項目，這又稱為*包含元素*。  
  
 宣告內容的層級如下：  
  
- *命名空間層級*-在來源檔案或命名空間中，但不在類別、結構、模組或介面中  
  
- *模組層級*-在類別、結構、模組或介面中，但不在程式或區塊內  
  
- 程式*層級*-在程式或區塊中（例如 `If` 或 `For` ）  
  
 下表顯示各種宣告的程式設計專案的預設存取層級，視其宣告內容而定。  
  
|宣告項目|命名空間層級|模組層級|程式層級|  
|----------------------|---------------------|------------------|---------------------|  
|Variable （[Dim 語句](dim-statement.md)）|不允許|`Private`（ `Public` 在中 `Structure` 不允許 `Interface` ）|`Public`|  
|常數（[Const 語句](const-statement.md)）|不允許|`Private`（ `Public` 在中 `Structure` 不允許 `Interface` ）|`Public`|  
|列舉（[Enum 語句](enum-statement.md)）|`Friend`|`Public`|不允許|  
|Class （[Class 語句](class-statement.md)）|`Friend`|`Public`|不允許|  
|Structure （[Structure 語句](structure-statement.md)）|`Friend`|`Public`|不允許|  
|Module （[模組語句](module-statement.md)）|`Friend`|不允許|不允許|  
|Interface （[介面語句](interface-statement.md)）|`Friend`|`Public`|不允許|  
|Procedure （[Function 語句](function-statement.md)， [Sub 語句](sub-statement.md)）|不允許|`Public`|不允許|  
|外部參考（[Declare 語句](declare-statement.md)）|不允許|`Public`（在中不允許 `Interface` ）|不允許|  
|運算子（[Operator 語句](operator-statement.md)）|不允許|`Public`（不允許在 `Interface` 或中使用 `Module` ）|不允許|  
|Property （[Property 語句](property-statement.md)）|不允許|`Public`|不允許|  
|Default 屬性（[預設值](../modifiers/default.md)）|不允許|`Public`（在中不允許 `Module` ）|不允許|  
|Event （[Event 語句](event-statement.md)）|不允許|`Public`|不允許|  
|Delegate （[委派語句](delegate-statement.md)）|`Friend`|`Public`|不允許|  
  
 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="see-also"></a>另請參閱

- [給](../modifiers/friend.md)
- [私用](../modifiers/private.md)
- [公開](../modifiers/public.md)
