---
title: 宣告項目特性
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], lifetime
- access levels, declared elements
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- elements [Visual Basic], programming
- scope [Visual Basic], declared elements
- lifetime [Visual Basic], declared elements
- declared elements [Visual Basic], access level
- data types [Visual Basic], declared elements
- declared elements [Visual Basic], visibility
ms.assetid: 1bc40fb8-b67c-4428-90a4-76b630ae2583
ms.openlocfilehash: 9d1e327c25689bed1405ea9a627da6232abb707b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392944"
---
# <a name="declared-element-characteristics-visual-basic"></a>宣告項目特性 (Visual Basic)
已宣告專案的*特性*是該專案的一個層面，會影響程式碼與它互動的方式。 每個宣告的元素都有一或多個相關聯的下列特性：  
  
- *資料類型*—元素可以保存的值，以及儲存這些值的方式。 如需詳細資訊，請參閱[資料類型](../../../language-reference/data-types/index.md)。  
  
- *存留*期-專案可供使用的執行時間期間。 如需詳細資訊，請參閱[Visual Basic 中的存留期](lifetime.md)。  
  
- *範圍*-可以參考專案但不限定其名稱的所有程式碼集合。 如需詳細資訊，請參閱[如何：控制變數的範圍](how-to-control-the-scope-of-a-variable.md)。  
  
- *存取層級*-程式碼用來利用專案的許可權。 如需詳細資訊，請參閱[如何：控制變數的可用性](how-to-control-the-availability-of-a-variable.md)。  
  
## <a name="characteristics-of-the-elements"></a>元素的特性  
 下表顯示已宣告的專案，以及套用至每一個專案的特性。  
  
|元素|資料類型|存留期|範圍<sup>1</sup>|存取層級|  
|-------------|---------------|--------------|------------------------|------------------|  
|變數|Yes|Yes|Yes|Yes|  
|持續性|是|否|是|Yes|  
|列舉型別|是|否|是|Yes|  
|結構|No|否|是|Yes|  
|屬性|Yes|Yes|Yes|Yes|  
|方法|否|是|Yes|Yes|  
|程式（ `Sub` 或 `Function` ）|否|是|Yes|Yes|  
|程序參數|Yes|Yes|是|No|  
|函數傳回|Yes|Yes|是|No|  
|運算子|是|否|是|Yes|  
|介面|No|否|是|Yes|  
|類別|No|否|是|Yes|  
|事件|No|否|是|Yes|  
|代理人|No|否|是|Yes|  
  
 <sup>1</sup>範圍有時稱為*可見度*。  
  
## <a name="see-also"></a>另請參閱

- [宣告的元素](index.md)
- [Declared Element Names](declared-element-names.md)
- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic 中的存留期](lifetime.md)
- [Visual Basic 中的範圍](scope.md)
- [Visual Basic 中的存取層級](access-levels.md)
- [資料類型](../data-types/index.md)
- [變數宣告](../variables/variable-declaration.md)
