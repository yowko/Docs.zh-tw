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
ms.openlocfilehash: 1ba25d830b1e7529bdf09c1195cc1fe7f9b2243b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354094"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>宣告內容和預設存取層級 (Visual Basic)
本主題描述哪些 Visual Basic 類型可以在哪些其他類型中宣告，以及其存取層級預設為（如果未指定）。  
  
## <a name="declaration-context-levels"></a>宣告內容層級  
 程式設計專案的宣告*內容*是宣告它之程式碼的區域。 這通常是另一個程式設計項目，這又稱為*包含元素*。  
  
 宣告內容的層級如下：  
  
- *命名空間層級*-在來源檔案或命名空間中，但不在類別、結構、模組或介面中  
  
- *模組層級*-在類別、結構、模組或介面中，但不在程式或區塊內  
  
- 程式*層級*-在程式或區塊中（例如 `If` 或 `For`）  
  
 下表顯示各種宣告的程式設計專案的預設存取層級，視其宣告內容而定。  
  
|宣告項目|命名空間層級|模組層級|程式層級|  
|----------------------|---------------------|------------------|---------------------|  
|Variable （[Dim 語句](../../../visual-basic/language-reference/statements/dim-statement.md)）|不允許|`Private` （在 `Structure`中`Public`，`Interface`中不允許）|`Public`|  
|常數（[Const 語句](../../../visual-basic/language-reference/statements/const-statement.md)）|不允許|`Private` （在 `Structure`中`Public`，`Interface`中不允許）|`Public`|  
|列舉（[Enum 語句](../../../visual-basic/language-reference/statements/enum-statement.md)）|`Friend`|`Public`|不允許|  
|Class （[Class 語句](../../../visual-basic/language-reference/statements/class-statement.md)）|`Friend`|`Public`|不允許|  
|Structure （[Structure 語句](../../../visual-basic/language-reference/statements/structure-statement.md)）|`Friend`|`Public`|不允許|  
|Module （[模組語句](../../../visual-basic/language-reference/statements/module-statement.md)）|`Friend`|不允許|不允許|  
|Interface （[介面語句](../../../visual-basic/language-reference/statements/interface-statement.md)）|`Friend`|`Public`|不允許|  
|Procedure （[Function 語句](../../../visual-basic/language-reference/statements/function-statement.md)， [Sub 語句](../../../visual-basic/language-reference/statements/sub-statement.md)）|不允許|`Public`|不允許|  
|外部參考（[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)）|不允許|`Public` （在 `Interface`中不允許）|不允許|  
|運算子（[Operator 語句](../../../visual-basic/language-reference/statements/operator-statement.md)）|不允許|`Public` （在 `Interface` 或 `Module`中不允許）|不允許|  
|Property （[Property 語句](../../../visual-basic/language-reference/statements/property-statement.md)）|不允許|`Public`|不允許|  
|Default 屬性（[預設值](../../../visual-basic/language-reference/modifiers/default.md)）|不允許|`Public` （在 `Module`中不允許）|不允許|  
|Event （[Event 語句](../../../visual-basic/language-reference/statements/event-statement.md)）|不允許|`Public`|不允許|  
|Delegate （[委派語句](../../../visual-basic/language-reference/statements/delegate-statement.md)）|`Friend`|`Public`|不允許|  
  
 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="see-also"></a>請參閱

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
