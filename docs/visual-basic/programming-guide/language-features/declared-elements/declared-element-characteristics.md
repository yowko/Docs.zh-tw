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
ms.openlocfilehash: 36c55475b4930dc6c3202d52ef742072d5cee3e1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075274"
---
# <a name="declared-element-characteristics-visual-basic"></a>宣告項目特性 (Visual Basic)

宣告專案的 *特性* 是該專案的一個層面，會影響程式碼與其互動的方式。 每個宣告的專案都有下列一或多個相關聯的特性：  
  
- *資料類型* ：元素可保存的值，以及其儲存這些值的方式。 如需詳細資訊，請參閱[資料類型](../../../language-reference/data-types/index.md)。  
  
- *存留* 期：專案可供使用的執行時間期間。 如需詳細資訊，請參閱 [Visual Basic 中的存留期](lifetime.md)。  
  
- *範圍* ：一組可以參考專案的程式碼，但不符合其名稱。 如需詳細資訊，請參閱 [如何：控制變數的範圍](how-to-control-the-scope-of-a-variable.md)。  
  
- *存取層級* ：程式碼用來利用元素的許可權。 如需詳細資訊，請參閱 [如何：控制變數的可用性](how-to-control-the-availability-of-a-variable.md)。  
  
## <a name="characteristics-of-the-elements"></a>元素的特性  

 下表顯示已宣告的專案以及套用至每一個專案的特性。  
  
|項目|資料類型|存留期|範圍 <sup>1</sup>|存取層級|  
|-------------|---------------|--------------|------------------------|------------------|  
|變數|是|是|是|是|  
|常數|是|否|是|是|  
|列舉型別|是|否|是|是|  
|結構|否|否|是|是|  
|屬性|是|是|是|是|  
|方法|否|是|是|是|  
|程式 (`Sub` 或 `Function`) |否|是|是|是|  
|程序參數|是|是|是|否|  
|函數傳回|是|是|是|否|  
|運算子|是|否|是|是|  
|介面|否|否|是|是|  
|類別|否|否|是|是|  
|事件|否|否|是|是|  
|代理人|否|否|是|是|  
  
 <sup>1</sup> 個範圍有時稱為 *可見度*。  
  
## <a name="see-also"></a>另請參閱

- [宣告的元素](index.md)
- [Declared Element Names](declared-element-names.md)
- [References to Declared Elements](references-to-declared-elements.md)
- [Visual Basic 中的存留期](lifetime.md)
- [Visual Basic 中的範圍](scope.md)
- [Visual Basic 中的存取層級](access-levels.md)
- [Data types (資料類型)](../data-types/index.md)
- [變數宣告](../variables/variable-declaration.md)
