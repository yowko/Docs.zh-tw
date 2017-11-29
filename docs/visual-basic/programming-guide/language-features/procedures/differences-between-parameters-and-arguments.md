---
title: "參數和引數之間的差異 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a>參數和引數之間的差異 (Visual Basic)
在大部分情況下，程序必須有一些情況中呼叫的相關資訊。 執行重複或共用的工作的程序會針對每個呼叫使用不同的資訊。 這項資訊包含變數、 常數和呼叫它時傳遞至程序的運算式。  
  
 若要將此資訊傳達給程序，程序會定義*參數*，和呼叫的程式碼傳遞*引數*至該參數。 您可以想像成停車參數，當做汽車的引數。 就如同在不同的時間，不同的汽車可以 park 停車空間中，呼叫程式碼可以不同引數傳遞至相同的參數每次它呼叫程序。  
  
## <a name="parameters"></a>參數  
 A*參數*表示程序必須有您在呼叫它時傳遞的值。 程序的宣告會定義它的參數。  
  
 當您定義`Function`或`Sub`程序，指定*參數清單*緊接在程序名稱的括號括住。 每個參數，指定名稱、 資料類型，以及傳遞機制 ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)或[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md))。 您也可能表示參數為選擇性。 這表示呼叫的程式碼不必值傳給它。  
  
 每個參數的名稱做為*區域變數*程序中。 使用參數名稱相同的方式使用任何其他變數。  
  
## <a name="arguments"></a>引數  
 *引數*表示當您呼叫程序傳遞至程序參數的值。 呼叫程序時，如果呼叫程式碼所提供的引數。  
  
 當您呼叫`Function`或`Sub`程序，包含*引數清單*緊接在程序名稱的括號括住。 每個引數會對應至清單中的相同位置中的參數。  
  
 相較於參數定義引數不會有名稱。 每個引數是運算式，其中可以包含零或多個變數、 常數和常值。 評估運算式的資料類型通常應符合為對應的參數定義的資料類型，並在任何情況下必須轉換成參數類型。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [Sub 程序](./sub-procedures.md)  
 [函式程序](./function-procedures.md)  
 [屬性程序](./property-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [如何：定義程序的參數](./how-to-define-a-parameter-for-a-procedure.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [遞迴程序](./recursive-procedures.md)  
 [程序多載化](./procedure-overloading.md)
