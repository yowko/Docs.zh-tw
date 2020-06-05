---
title: 如何：移入和移出變數資料
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: fe19a6160623aa9ea867becdf7a15b51319abf45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410434"
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>如何：移入和移出變數資料 (Visual Basic)

您可以藉由將變數名稱放在指派語句的左邊，將值儲存在變數中。

## <a name="putting-data-in-a-variable"></a>將資料放入變數中

#### <a name="to-store-a-value-in-a-variable"></a>將值儲存在變數中

- 在指派語句的左邊使用變數名稱。

    下列範例會設定變數的值 `alpha` 。

    ```vb
    alpha = (beta * 6.27) / (gamma + 2.1)
    ```

    在指派語句的右邊產生的值會儲存在變數中。

## <a name="getting-data-from-a-variable"></a>從變數取得資料

您可以藉由在運算式中包含變數名稱，來取出變數的值。

#### <a name="to-retrieve-a-value-from-a-variable"></a>若要從變數中取出值

- 在運算式中使用變數名稱。 除了定義常數值的運算式以外，您可以在任何可使用常數或常值的地方使用變數。

  \-或-

- 在指派語句中的等號（）後面使用變數名稱 `=` 。

  下列範例會讀取變數的值 `startValue` ，然後在運算式中使用變數的值 `counter` 。

  ```vb
  counter = startValue
  cellValue = (counter + 5) ^ 2
  ```

  變數的值會以常數的形式參與運算式，然後儲存在指派語句左側的變數或屬性中。

## <a name="see-also"></a>另請參閱

- [變數](index.md)
- [變數宣告](variable-declaration.md)
- [物件變數](object-variables.md)
