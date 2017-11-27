---
title: "參數陣列 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a>參數陣列 (Visual Basic)
通常，您無法呼叫具有多個引數數目比程序宣告指定的程序。 當您需要了不定數量的引數時，您可以宣告*參數陣列*，可讓程序以接受的參數值陣列。 您不必知道參數陣列中的項目數，當您定義的程序。 陣列大小取決於個別的程序的每個呼叫。  
  
## <a name="declaring-a-paramarray"></a>宣告參數陣列  
 您使用[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)關鍵字來代表在參數清單中的參數陣列。 可套用下列規則：  
  
-   程序可以定義只有一個參數的陣列，而且它必須是程序定義中的最後一個參數。  
  
-   參數陣列必須以傳值。 良好的程式設計作法明確包含[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)程序定義中的關鍵字。  
  
-   參數陣列會自動為選用。 其預設值是空的一維陣列，參數陣列的項目類型。  
  
-   參數陣列之前的所有參數必須都是必要的。 參數陣列必須是唯一的選擇性參數。  
  
## <a name="calling-a-paramarray"></a>呼叫的參數陣列  
 當您呼叫定義的參數陣列的程序時，您可以在任何一種以下列方式提供引數：  
  
-   執行任何動作，也就是您可以省略[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引數。 在此情況下，空的陣列會傳遞至程序。 您也可以傳遞[Nothing](../../../../visual-basic/language-reference/nothing.md)關鍵字，使用相同的效果。  
  
-   任意數目的引數，並以逗號分隔的清單。 每個引數的資料類型必須是隱含地轉換成`ParamArray`項目類型。  
  
-   具有相同的項目型別參數陣列的項目類型的陣列。  
  
 在所有情況下，此程序中的程式碼會將參數的陣列視為具有相同的資料類型之項目的一維陣列`ParamArray`資料型別。  
  
> [!IMPORTANT]
>  只要處理陣列，其中可能會無限期地大，會有風險的造成滿溢內部應用程式的容量。 如果您接受參數陣列時，您應該測試呼叫的程式碼傳遞給它之陣列的大小。 如果您的應用程式而言太大，請採取適當的步驟。 如需詳細資訊，請參閱[陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)。  
  
## <a name="example"></a>範例  
 下列範例會定義和呼叫的函式`calcSum`。 `ParamArray`參數修飾詞`args`啟用接受可變數目的引數的函式。  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 下列範例定義的參數陣列的程序，並將輸出傳遞至參數陣列的所有陣列項目的值。  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [依位置和名稱傳遞引數](./passing-arguments-by-position-and-by-name.md)  
 [選擇性參數](./optional-parameters.md)  
 [程序多載化](./procedure-overloading.md)  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
