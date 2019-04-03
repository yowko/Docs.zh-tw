---
title: HOW TO：將資料移入和移出變數 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: 30d1c0ab91724ac556e59b272782513ee8b8067b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818527"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>HOW TO：將資料移入和移出變數 (Visual Basic)
您將變數的名稱放在指派陳述式左邊值儲存在變數中。  
  
## <a name="putting-data-in-a-variable"></a>將資料放在變數中  
  
#### <a name="to-store-a-value-in-a-variable"></a>若要儲存在變數中的值  
  
-   在指派陳述式左邊使用的變數名稱。  
  
     下列範例會設定變數的值`alpha`。  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     指派陳述式右側所產生的值會儲存在變數中。  
  
## <a name="getting-data-from-a-variable"></a>從變數取得資料  
 您可以在運算式中包括變數的名稱擷取變數的值。  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>從變數擷取值  
  
-   在運算式中使用變數的名稱。 您可以使用變數任何地方您可以使用常數或常值，除了中定義的常數值的運算式。  
  
     -或-  
  
-   使用下列相等的變數名稱 (`=`) 登入在指派陳述式。  
  
     下列範例會讀取變數的值`startValue`，然後使用變數的值`counter`在運算式中。  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     變數的值會參與運算式，就如同常數會，並再儲存在變數或指派陳述式左邊的屬性。  
  
## <a name="see-also"></a>另請參閱

- [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
