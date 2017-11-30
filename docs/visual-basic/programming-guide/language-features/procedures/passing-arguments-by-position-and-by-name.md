---
title: "依位置和名稱傳遞引數 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>依位置和名稱傳遞引數 (Visual Basic)
當您呼叫`Sub`或`Function`程序中，您可以傳遞引數*依位置*— 在程序的定義中的出現順序，或您可以將其傳遞*依名稱*，而不考慮位置。  
  
 當您依名稱傳遞引數時，您指定的引數的宣告名稱後接冒號和等號 (`:=`)，後面接著引數值。 您可以提供以任何順序指定的引數。  
  
 例如，下列`Sub`程序會採用三個引數：  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 當您呼叫此程序時，您可以提供的引數的位置、 名稱，或使用兩者的混合。  
  
## <a name="passing-arguments-by-position"></a>依位置傳遞引數  
 您可以呼叫此程序`studentInfo`的引數依位置傳遞，並以逗號分隔，如下列範例所示：  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 如果您省略選擇性引數位置引數清單中的，您必須保留其所在位置，請使用逗號。 下列範例會呼叫`studentInfo`沒有`age`引數：  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>依名稱傳遞引數  
 或者，您可以呼叫`studentInfo`依名稱傳遞引數時，也以逗號分隔，如下列範例所示：  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>混合位置和名稱引數  
 您可以提供引數位置和名稱，在單一程序呼叫中，如下列範例所示：  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 在上述範例中，沒有額外的逗號是為了保留位置省略`age`引數，因為`birth`依名稱傳遞。  
  
 混合位置和名稱、 位置引數提供的引數時，必須放在第一次。 一旦您依名稱提供引數，其餘的引數都必須依名稱。  
  
## <a name="supplying-optional-arguments-by-name"></a>提供選擇性引數名稱  
 當您呼叫具有一個以上的選擇性引數的程序時，依名稱傳遞引數會特別有用。 如果您依名稱提供引數，您不必用連續逗號來表示遺漏位置引數。 依名稱傳遞引數也可讓您更輕鬆地追蹤您傳遞和哪些省略了哪些引數。  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a>依名稱提供引數的限制  
 您無法使用名稱來避免輸入必要的引數傳遞引數。 您可以省略選擇性引數。  
  
 您無法依名稱傳遞參數陣列。 這是因為當您呼叫程序，提供了不定數量的參數陣列中，以逗號分隔的引數，編譯器無法將多個引數，與單一的名稱。  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)  
 [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)  
 [選擇性參數](./optional-parameters.md)  
 [參數陣列](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
