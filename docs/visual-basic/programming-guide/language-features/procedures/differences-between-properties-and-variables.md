---
title: Visual Basic 中屬性和變數的差別
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
ms.openlocfilehash: de4800e23519c2cc1c8b2b219287b9fa018b9bbf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842898"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic 中屬性和變數的差別
變數和屬性都代表您可以存取的值。 不過，有儲存體和實作差異。  
  
## <a name="variables"></a>變數  
 A*變數*直接對應至記憶體位置。 您定義的單一宣告陳述式的變數。 變數可以是*區域變數*、 定義程序內，只能在該程序，也可以很*成員變數*，定義在模組、 類別或結構，但不是能在任何程序。 成員變數亦稱為*欄位*。  
  
## <a name="properties"></a>屬性  
 A*屬性*是一個模組、 類別或結構上定義的資料元素。 您定義的屬性之間的程式碼區塊`Property`和`End Property`陳述式。 程式碼區塊包含`Get`程序，`Set`程序，或兩者。 這些程序稱為*屬性程序*或是*屬性存取子*。 除了擷取或儲存屬性的值，它們也可以執行自訂動作，例如更新存取計數器。  
  
## <a name="differences"></a>差異  
 下表顯示變數和屬性之間的一些重要差異。  
  
|差異點|變數|屬性|  
|-------------------------|--------------|--------------|  
|宣告|單一宣告陳述式|系列的程式碼區塊中的陳述式|  
|實作|單一儲存體位置|可執行程式碼 （屬性程序）|  
|存放裝置|直接相關聯的變數值|通常會有提供之外的屬性包含類別或模組的內部儲存體<br /><br /> 屬性的值可能會或可能不會存在做為預存的項目<sup>1</sup>|  
|可執行程式碼|None|必須至少一個程序|  
|讀取和寫入權限|讀寫或唯讀|讀取/寫入、 唯讀或唯寫|  
|自訂動作 （除了接受或傳回值）|不可能|可以執行設定或擷取屬性值的一部分|  
  
 <sup>1</sup>不同變數中，於屬性的值可能不直接對應到儲存體的單一項目。 儲存體可能會分割成片段，方便或安全性，或值可能會以加密形式儲存。 在這些情況下`Get`程序會組合在一起，或解密儲存的值，而`Set`程序會加密新的值，或將它分割為組成的儲存體。 屬性值在此情況下可能是暫時的例如一天時間，`Get`程序會計算會即時每次存取屬性。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合的存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：宣告，並在 Visual Basic 中呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值放在屬性中](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
