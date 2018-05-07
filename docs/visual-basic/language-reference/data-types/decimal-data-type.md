---
title: Decimal 資料類型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
ms.openlocfilehash: 9e256e93d7857c8674a1d711fa9cafd3ed9a29f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="decimal-data-type-visual-basic"></a>Decimal 資料類型 (Visual Basic)
保存帶正負號的 128 位元 （16 位元） 值，表示以可變倍率 10 倍的 96 位元 （12 個位元組） 整數數字。 縮放比例指定小數點右邊位數的數目它的範圍是從 0 到 28。 小數位數為 0 （沒有小數位數），最大的可能值是 + /-79228162514264337593543950335 (+ /-7.9228162514264337593543950335E + 28)。 具有 28 的小數位數，最大值是 + /--7.9228162514264337593543950335，和最小的非零值是 + /-0.0000000000000000000000000001 （+ /-1E 28)。  
  
## <a name="remarks"></a>備註  
 `Decimal`資料類型提供數個有效位數的最大數目。 它支援高達 29 個有效位數，而且可以代表值超過 7.9228 x 10 ^28。 它特別適用於計算，例如財務、，需要大量的數字，但不能容忍捨入錯誤。  
  
 `Decimal` 的預設值為 0。  
  
## <a name="programming-tips"></a>程式設計提示  
  
-   **有效位數。** `Decimal` 不是浮點數資料類型。 `Decimal`結構包含二進位整數值，以及正負號位元和縮放比例，指定值的哪些部分是十進位小數的整數。 因為這個緣故，`Decimal`數字比浮點類型的記憶體中有更精確地表示法 (`Single`和`Double`)。  
  
-   **效能。** `Decimal`資料類型是最慢的所有數字的類型。 您應該衡量精確度和效能，再選擇的資料類型的重要性。  
  
-   **擴展。** `Decimal`資料類型可擴展成`Single`或`Double`。 這表示您可以將轉換`Decimal`而不會發生這些類型的任何一個<xref:System.OverflowException?displayProperty=nameWithType>錯誤。  
  
-   **尾端零。** Visual Basic 不會儲存尾端零`Decimal`常值。 不過，`Decimal`變數會保留運算資源取得任何尾端零。 下列範例將說明這點。  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     輸出`MsgBox`在上述範例如下所示：  
  
     d1 = 2.375，d2 = 1.625，d3 = 4.000，d4 = 4  
  
-   **類型字元。** 將常值類型字元 `D` 附加到常值，會強制其成為 `Decimal` 資料類型。 將識別項類型字元 `@` 附加到任何識別項，會強制其成為 `Decimal`。  
  
-   **架構類型。** 在 .NET Framework 中對應的類型為 <xref:System.Decimal?displayProperty=nameWithType> 結構。  
  
## <a name="range"></a>範圍  
 您可能需要使用`D`輸入字元到大型值指派給`Decimal`變數或常數。 這是因為編譯器會解譯為常值`Long`除非常值類型字元後面常值，如下列範例所示。  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 宣告`bigDec1`不會產生溢位，因為指派給它的值落在範圍內`Long`。 `Long`可指派值給`Decimal`變數。  
  
 宣告`bigDec2`會產生溢位錯誤，因為指派給它的值太大的`Long`。 因為數值常值第一次無法解譯為`Long`，無法指派給`Decimal`變數。  
  
 如`bigDec3`，常值類型字元`D`可以解決問題，可能會強制編譯器將解譯為常值`Decimal`而不是做為`Long`。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [資料類型](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Single 資料類型](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [Double 資料類型](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [類型轉換函式](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [轉換摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [有效率地使用資料類型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
