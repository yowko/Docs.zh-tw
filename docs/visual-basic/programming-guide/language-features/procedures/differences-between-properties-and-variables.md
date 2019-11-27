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
ms.openlocfilehash: bbed3248840803d36607a67c8373fed15c07445f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341214"
---
# <a name="differences-between-properties-and-variables-in-visual-basic"></a>Visual Basic 中屬性和變數的差別
變數和屬性都代表您可以存取的值。 不過，儲存體和實作為差異。  
  
## <a name="variables"></a>變數  
 *變數*會直接對應到記憶體位置。 您可以使用單一宣告語句來定義變數。 變數可以是在程式內定義的*區域變數*，而且只能在該程式內使用，或者可以是在模組、類別或結構中定義，但不在任何程式內的*成員變數*。 成員變數也稱為*欄位*。  
  
## <a name="properties"></a>屬性  
 「*屬性*」（property）是在模組、類別或結構上定義的資料元素。 您可以使用 `Property` 和 `End Property` 語句之間的程式碼區塊來定義屬性。 程式碼區塊包含 `Get` 程式、`Set` 程式或兩者。 這些程式稱為*屬性程式*或*屬性存取*子。 除了抓取或儲存屬性的值之外，它們也可以執行自訂動作，例如更新存取計數器。  
  
## <a name="differences"></a>差異  
 下表顯示變數和屬性之間的一些重要差異。  
  
|差異點|變數|屬性|  
|-------------------------|--------------|--------------|  
|宣告|單一宣告語句|程式碼區塊中的一連串語句|  
|實作|單一儲存位置|可執行程式碼（屬性程式）|  
|存放裝置|直接與變數的值相關聯|通常在屬性的包含類別或模組之外，無法使用內部儲存體<br /><br /> 屬性的值不一定會以預存元素的形式存在<sup>1</sup>|  
|可執行程式碼|無|必須至少有一個程式|  
|讀取和寫入存取權|讀取/寫入或唯讀|讀取/寫入、唯讀或僅限寫入|  
|自訂動作（除了接受或傳回值以外）|不可能|可以做為設定或抓取屬性值的一部分來執行|  
  
 <sup>1</sup>與變數不同的是，屬性的值可能不會直接對應至單一的儲存專案。 儲存區可能會分割成方便或安全性的部分，或者值可能會以加密形式儲存。 在這些情況下，`Get` 程式會組合部分或解密儲存的值，而 `Set` 程式會加密新的值，或將它分割成構成儲存體。 屬性值可能是暫時的，像是一天中的時間，在這種情況下，`Get` 程式會在每次您存取屬性時即時計算它。  
  
## <a name="see-also"></a>另請參閱

- [屬性程序](./property-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [如何：建立屬性](./how-to-create-a-property.md)
- [如何：宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)
- [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)
- [如何：在 Visual Basic 中宣告及呼叫預設屬性](./how-to-declare-and-call-a-default-property.md)
- [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)
- [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
