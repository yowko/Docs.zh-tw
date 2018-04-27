---
title: 字串與其他類型之間的轉換 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82473d59d6b6aac21f2d7f2a0c9748217a61985f
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>字串與其他類型之間的轉換 (Visual Basic)
您可以將數字轉換`Boolean`，或日期/時間值`String`。 您也可以反向轉換，從字串值為數值， `Boolean`，或`Date`— 提供字串的內容可以解譯為有效的目的地資料類型的值。 如果它們不會發生執行階段錯誤。  
  
 所有這些指派任一方向的轉換縮小轉換。 您應該使用類型轉換關鍵字 (`CBool`， `CByte`， `CDate`， `CDbl`， `CDec`， `CInt`， `CLng`， `CSByte`， `CShort`， `CSng`， `CStr`，`CUInt`， `CULng`， `CUShort`，和`CType`)。 <xref:Microsoft.VisualBasic.Strings.Format%2A>和<xref:Microsoft.VisualBasic.Conversion.Val%2A>函式可讓您轉換字串與數字之間的額外控制。  
  
 如果您已定義類別或結構，您可以定義類型之間的轉換運算子`String`和類別或結構的類型。 如需詳細資訊，請參閱[如何： 定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。  
  
## <a name="conversion-of-numbers-to-strings"></a>數字轉換為字串  
 您可以使用`Format`函式，將數字轉換為格式化的字串，其中可以包括不僅適當的數字，但也格式化符號，例如貨幣符號 (例如`$`)，千位分隔符號或*數字分位符號*(例如`,`)，以及小數分隔符號 (例如`.`)。 `Format` 會自動使用適當的符號，根據**地區選項**指定在 Windows 中設定**控制台**。  
  
 請注意，串連 (`&`) 運算子可以將數字轉換成字串以隱含方式，如下列範例所示。  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>字串轉換成數字  
 您可以使用`Val`函式來明確地將字串中的數字轉換為數值。 `Val` 讀取字串，直到它遇到數字、 空格、 索引標籤、 換行字元或句號以外的字元。 將序列"& O"和"& H"alter 基底的數字系統，並終止掃描。 停止讀取，直到`Val`將所有適當的字元轉換為數值。 例如，下列陳述式傳回值`141.825`。  
  
 `Val("   14   1.825 miles")`  
  
 當 Visual Basic 會將字串轉換為數值時，它會使用**地區選項**指定在 Windows 中設定**控制台**解譯千分位分隔符號、 小數點，和貨幣符號。 這表示，轉換可能會成功的其中一個下但沒有其他設定。 例如，`"$14.20"`是可接受的英文 （美國） 地區設定，但不是在法文地區設定。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [擴展和縮小轉換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [隱含和明確轉換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [如何： 將物件轉換成 Visual Basic 中的另一個類型](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [以 .NET Framework 為基礎的國際應用程式簡介](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
