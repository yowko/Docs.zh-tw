---
title: "如何：移入和移出變數資料 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>如何：移入和移出變數資料 (Visual Basic)
您將變數的名稱放在指派陳述式左邊將值儲存在變數中。  
  
## <a name="putting-data-in-a-variable"></a>將資料放在變數中  
  
#### <a name="to-store-a-value-in-a-variable"></a>將值儲存在變數中  
  
-   指派陳述式的左邊使用變數名稱。  
  
     下列範例會設定變數的值`alpha`。  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     產生的指派陳述式右邊的值會儲存在變數中。  
  
## <a name="getting-data-from-a-variable"></a>從變數取得資料  
 您可以在運算式中包括變數名稱擷取變數的值。  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>若要從變數擷取值  
  
-   在運算式中使用變數名稱。 您可以使用變數任何地方您可以使用常數或常值，除了在定義常數值的運算式。  
  
     -或-  
  
-   使用變數名稱後面，等於 (`=`) 登入指派陳述式。  
  
     下列範例會讀取變數的值`startValue`，然後使用變數的值`counter`在運算式中。  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     變數的值加入運算式，就如同常數會，然後儲存在變數或指派陳述式左邊的屬性。  
  
## <a name="see-also"></a>另請參閱  
 [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
