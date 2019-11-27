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
ms.openlocfilehash: 621dec7537e9c993024e271b96ab8706baf89885
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350115"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>有效率地使用資料類型 (Visual Basic)
未宣告的變數和不含資料類型的變數會被指派 `Object` 資料類型。 這可讓您快速撰寫程式，但它可能會導致執行速度變慢。

## <a name="strong-typing"></a>強式類型
 指定所有變數的資料類型稱為*強式類型*。 使用強型別有幾個優點：

- 它會針對您的變數啟用 IntelliSense 支援。 這可讓您在程式碼中輸入時，看到其屬性和其他成員。

- 它會利用編譯器類型檢查。 這會捕捉可能因為溢位錯誤而在執行時間失敗的語句。 它也會攔截不支援之物件上方法的呼叫。

- 這會導致程式碼的執行速度更快。

## <a name="most-efficient-data-types"></a>最有效率的資料類型
 對於永不包含小數的變數而言，整數資料類型比非整數類型更有效率。 在 Visual Basic 中，`Integer` 和 `UInteger` 是最有效率的數數值型別。

 就小數而言，`Double` 是最有效率的資料類型，因為目前平臺上的處理器會以雙精確度執行浮點運算。 不過，具有 `Double` 的作業不如使用整數類資料類型（例如 `Integer`）的速度快。

## <a name="specifying-data-type"></a>指定資料類型
 使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)來宣告特定類型的變數。 您可以使用[Public](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[Private](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，同時指定其存取層級，如下列範例所示。

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a>字元轉換
 `AscW` 和 `ChrW` 函數會以 Unicode 運作。 您應該在喜好設定中使用它們來 `Asc` 和 `Chr`，這必須轉譯成 Unicode。

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [數值資料類型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [使用 IntelliSense](/visualstudio/ide/using-intellisense)
