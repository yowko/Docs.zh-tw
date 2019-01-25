---
title: 參數和引數之間的差異 (Visual Basic)
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
ms.openlocfilehash: ec7c92975bc056fd740033b602b15cd1611c44d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694031"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>參數和引數之間的差異 (Visual Basic)
在大部分情況下，程序必須有一些情況在其中呼叫的相關資訊。 執行重複或共用工作的程序會針對每個呼叫中使用不同的資訊。 這項資訊是由變數、 常數和您傳遞至程序時呼叫它的運算式所組成。  
  
 若要將此資訊傳達給程序，程序會定義*參數*，並呼叫程式碼傳遞*引數*至該參數。 您可以想像成停車參數，為汽車的引數。 就如同不同汽車可以 park 停車位空間中，在不同的時間，則呼叫端程式碼可以在每一次，它會呼叫程序傳遞不同的引數至相同的參數。  
  
## <a name="parameters"></a>參數  
 A*參數*表示程序必須有您在呼叫它時傳遞的值。 程序的宣告會定義其參數。  
  
 當您定義`Function`或是`Sub`程序中，指定*參數清單*緊接在程序名稱的括號括住。 針對每個參數，指定名稱、 資料類型和傳遞機制 ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或是[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md))。 您也可以指定參數為選擇性。 這表示呼叫端程式碼不需要值傳給它。  
  
 每個參數的名稱做為*區域變數*程序中。 使用參數名稱相同的方式使用任何其他變數。  
  
## <a name="arguments"></a>引數  
 *引數*表示當您呼叫程序時，您傳遞至程序參數的值。 呼叫程序時，呼叫程式碼會提供引數。  
  
 當您呼叫`Function`或是`Sub`程序，包括*引數清單*緊接在程序名稱的括號括住。 每個引數會對應至清單中的相同位置中的參數。  
  
 相較於參數定義引數不會有名稱。 每個引數是運算式，其中可以包含零或多個變數、 常數和常值。 評估的運算式的資料類型通常應該符合定義之對應參數的資料類型，並在任何情況下，都必須是將它轉換成參數類型。  
  
## <a name="see-also"></a>另請參閱
- [程序](./index.md)
- [Sub 程序](./sub-procedures.md)
- [函式程序](./function-procedures.md)
- [屬性程序](./property-procedures.md)
- [運算子程序](./operator-procedures.md)
- [如何：如需程序來定義參數](./how-to-define-a-parameter-for-a-procedure.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [遞迴程序](./recursive-procedures.md)
- [程序多載化](./procedure-overloading.md)
