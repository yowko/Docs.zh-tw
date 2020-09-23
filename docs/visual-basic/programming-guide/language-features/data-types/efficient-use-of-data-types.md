---
title: 有效率地使用資料類型
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 7f446b264dcb5c05ed6ddfba34acbbf66be0e447
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91084108"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>有效率地使用資料類型 (Visual Basic)

未宣告的變數和沒有資料類型宣告的變數會被指派 `Object` 資料類型。 這可讓您輕鬆地快速撰寫程式，但這可能會導致這些程式執行速度變得更慢。

## <a name="strong-typing"></a>強型別

 指定所有變數的資料類型稱為 *強*型別。 使用強型別有幾個優點：

- 它可為您的變數啟用 IntelliSense 支援。 當您在程式碼中輸入時，這可讓您查看其屬性和其他成員。

- 它會利用編譯器類型檢查。 這會攔截在執行時間因為溢位之類的錯誤而失敗的語句。 它也會攔截對不支援它們之物件的方法呼叫。

- 這會導致程式碼的執行速度更快。

## <a name="most-efficient-data-types"></a>最有效率的資料類型

 對於永遠不包含分數的變數而言，整數資料類型比非整數類型更有效率。 在 Visual Basic 中， `Integer` 和 `UInteger` 是最有效率的數數值型別。

 對於小數數位而言， `Double` 是最有效率的資料類型，因為目前平臺上的處理器會以雙精確度執行浮點運算。 不過，使用的作業 `Double` 不像整數類資料類型一樣快 `Integer` 。

## <a name="specifying-data-type"></a>指定資料類型

 使用 [Dim 語句](../../../language-reference/statements/dim-statement.md) 來宣告特定型別的變數。 您可以使用 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)或 [Private](../../../language-reference/modifiers/private.md) 關鍵字同時指定其存取層級，如下列範例所示。

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>字元轉換

 和函式會 `AscW` `ChrW` 以 Unicode 運作。 您應該將其喜好設定為 `Asc` 和 `Chr` ，而必須將其轉譯成 Unicode 或從中轉換。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Data types (資料類型)](index.md)
- [數值資料類型](numeric-data-types.md)
- [變數宣告](../variables/variable-declaration.md)
- [使用 IntelliSense](/visualstudio/ide/using-intellisense)
