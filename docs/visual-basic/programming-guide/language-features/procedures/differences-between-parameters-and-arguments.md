---
title: 參數和引數之間的差異
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: dd0a62b6567f3e74763b7f2e9b96803c193c7976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403352"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>參數和引數之間的差異 (Visual Basic)
在大部分情況下，程式必須有一些有關已呼叫它的情況的資訊。 執行重複或共用工作的程式會針對每個呼叫使用不同的資訊。 這項資訊是由您在呼叫它時傳遞給程式的變數、常數和運算式所組成。  
  
 為了將此資訊傳達給程式，此程式會定義一個*參數*，而呼叫的程式碼會將*引數*傳遞給該參數。 您可以將參數視為停車空間，並將引數視為汽車。 就如同不同的汽車可以在停車空間中的不同時間靜止，呼叫程式碼可以在每次呼叫程式時，將不同的引數傳遞至相同的參數。  
  
## <a name="parameters"></a>參數  
 *參數*代表當您呼叫它時，程式預期會傳遞的值。 程式的宣告會定義其參數。  
  
 當您定義或程式時 `Function` `Sub` ，您會緊接在程式名稱後面的括弧中指定*參數清單*。 針對每個參數，您可以指定名稱、資料類型和傳遞機制（[ByVal](../../../language-reference/modifiers/byval.md)或[ByRef](../../../language-reference/modifiers/byref.md)）。 您也可以指出參數是選擇性的。 這表示呼叫程式碼不需要傳遞值給它。  
  
 在程式中，每個參數的名稱都可做為*區域變數*。 使用參數名稱的方式與使用任何其他變數相同。  
  
## <a name="arguments"></a>引數  
 *引數*代表當您呼叫程式時，傳遞給 procedure 參數的值。 呼叫程式碼會在呼叫程式時提供引數。  
  
 當您呼叫或程式時 `Function` `Sub` ，您會緊接在程式名稱後面的括弧中包含*引數清單*。 每個引數都會對應至清單中相同位置的參數。  
  
 相對於參數定義，引數沒有名稱。 每個引數都是運算式，其中可以包含零個或多個變數、常數和常值。 已評估運算式的資料類型通常應該符合針對對應參數所定義的資料類型，而且在任何情況下都必須可轉換為參數類型。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [Function 程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [如何：定義程序的參數](./how-to-define-a-parameter-for-a-procedure.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [遞迴程序](./recursive-procedures.md)
- [程序多載化](./procedure-overloading.md)
