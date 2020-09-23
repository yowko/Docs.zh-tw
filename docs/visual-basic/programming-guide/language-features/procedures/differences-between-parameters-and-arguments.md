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
ms.openlocfilehash: 0ad9104f347205cebc6e078aac246a413c0d9b78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057841"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>參數和引數之間的差異 (Visual Basic)

在大部分情況下，程式必須有一些有關呼叫它的情況的資訊。 執行重複或共用工作的程式會針對每個呼叫使用不同的資訊。 這項資訊是由您在呼叫過程中傳遞給程式的變數、常數和運算式所組成。  
  
 為了將此資訊傳達給程式，程式會定義 *參數*，呼叫程式碼會將 *引數* 傳遞給該參數。 您可以將參數視為停車空間，而將引數視為汽車。 如同不同的汽車可以在不同時間的停車空間中駐留，呼叫程式碼可以在每次呼叫程式時，將不同的引數傳遞至相同的參數。  
  
## <a name="parameters"></a>參數  

 *參數*代表程式要求您在呼叫時傳遞的值。 程式的宣告會定義其參數。  
  
 當您定義或程式時 `Function` `Sub` ，您可以緊接在程式名稱後面的括弧中指定 *參數清單* 。 針對每個參數，您可以指定名稱、資料類型，以及 ([ByVal](../../../language-reference/modifiers/byval.md) 或 [ByRef](../../../language-reference/modifiers/byref.md)) 的傳遞機制。 您也可以指出參數是選擇性的。 這表示呼叫程式碼不需要傳遞值給它。  
  
 每個參數的名稱會當做程式中的 *區域變數* 。 您可以使用參數名稱，就像使用任何其他變數一樣。  
  
## <a name="arguments"></a>引數  

 *引數*代表當您呼叫程式時，您傳遞給程式參數的值。 呼叫程式碼會在呼叫程式時提供引數。  
  
 當您呼叫 `Function` 或 `Sub` 程式時，您會在程式名稱後面緊接著括弧中包含 *引數清單* 。 每個引數都對應至清單中相同位置的參數。  
  
 相對於參數定義，引數沒有名稱。 每個引數都是一個運算式，它可以包含零或多個變數、常數和常值。 評估運算式的資料類型通常應該符合為對應參數定義的資料類型，而且在任何情況下，它必須可轉換為參數類型。  
  
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
