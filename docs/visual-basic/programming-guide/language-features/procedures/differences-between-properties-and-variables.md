---
title: 屬性和變數之間的差異
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- variables [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- variables [Visual Basic], definition
- Visual Basic code, variables
- Visual Basic code, properties
- properties [Visual Basic], values
- properties [Visual Basic], defined
- variables [Visual Basic], and properties
- properties [Visual Basic], and variables
ms.assetid: 7a03a8be-5381-431f-bd7c-16e887e4e07b
ms.openlocfilehash: 95bafcaca98e1a0fbdd62a550291c8ece932c1ba
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075027"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic 中屬性和變數的差別

變數和屬性都代表您可以存取的值。 不過，儲存體和執行之間有一些差異。  
  
## <a name="variables"></a>變數  

 *變數*會直接對應到記憶體位置。 您可以使用單一宣告語句來定義變數。 變數可以是在程式內定義的 *區域變數*，而且只能在該程式中使用，也可以是在模組、類別或結構中定義的 *成員變數*，而不是在任何程式內。 成員變數也稱為 *欄位*。  
  
## <a name="properties"></a>屬性  

 *屬性*是在模組、類別或結構上定義的資料元素。 您可以使用和語句之間的程式碼區塊來定義屬性 `Property` `End Property` 。 程式碼區塊包含程式 `Get` 、程式 `Set` 或兩者。 這些程式稱為 *屬性程式* 或 *屬性存取*子。 除了抓取或儲存屬性的值之外，也可以執行自訂動作，例如更新存取計數器。  
  
## <a name="differences"></a>差異  

 下表顯示變數和屬性之間的一些重要差異。  
  
|差異點|變數|屬性|  
|-------------------------|--------------|--------------|  
|宣告|Single 宣告語句|程式碼區塊中的語句系列|  
|實作|單一儲存體位置|可執行程式碼 (屬性程式) |  
|儲存體|直接關聯至變數的值|通常無法在屬性的包含類別或模組之外使用內部儲存體<br /><br /> 屬性的值不一定會以預存元素<sup>1</sup>的形式存在|  
|可執行程式碼|無|至少必須有一個程式|  
|讀取和寫入存取權|讀取/寫入或唯讀|讀/寫、唯讀或僅限寫入|  
|除了接受或傳回值之外，還 (自訂動作) |不可能|可作為設定或抓取屬性值的一部分來執行|  
  
 <sup>1</sup> 與變數不同的是，屬性的值可能不會直接對應到儲存區的單一專案。 儲存體可能會分割成方便或安全性的部分，或者值可能會以加密形式儲存。 在這些情況下，程式 `Get` 會組合片段或解密儲存的值，而此程式 `Set` 會加密新的值，或將其分割成構成的儲存體。 屬性值可能是暫時的，就像是一天中的時間，在這種情況下，程式 `Get` 會在您每次存取屬性時將它即時計算。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Dim 陳述式](../../../language-reference/statements/dim-statement.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
