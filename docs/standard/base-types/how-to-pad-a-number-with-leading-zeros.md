---
title: 如何：以前置字元零來填補數字
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ce3b59db027ffebf616a035b018629cb7aed30c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a>如何：以前置字元零來填補數字
如果整數要加上前置零，您可以使用具有精確度規範的 "D" [標準數值格式字串](../../../docs/standard/base-types/standard-numeric-format-strings.md)。 如果整數和浮點數都要加上前置零，您可以使用[自訂數值格式字串](../../../docs/standard/base-types/custom-numeric-format-strings.md)。 此主題示範如何使用這兩種方法，以前置零填補數值。  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>以前置零將整數填補至特定長度  
  
1.  決定您要整數值顯示的位數下限。 在此數值中包含任何前置數。  
  
2.  決定要將整數顯示為十進位值或十六進位值。  
  
    -   若要將整數顯示為十進位值，請呼叫其 `ToString(String)` 方法，然後傳遞字串 "D*n*" 以作為 `format` 參數的值，其中 *n* 代表字串的長度下限。  
  
    -   若要將整數顯示為十六進位值，請呼叫其 `ToString(String)` 方法，然後傳遞字串 "X*n*" 以作為 `format` 參數的值，其中 *n* 代表字串的長度下限。  
  
     您也可以在使用[複合格式](../../../docs/standard/base-types/composite-formatting.md)的方法 (例如 <xref:System.String.Format%2A> 或 <xref:System.Console.WriteLine%2A>) 中使用格式字串。  
  
 下列範例會使用前置零來將數個整數值格式化，讓格式化數值的總長度至少為 8 個字元。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>以特定數目的前置零填補整數  
  
1.  決定您想要讓整數值顯示多少個前置零。  
  
2.  決定要將整數顯示為十進位值或十六進位值。 若要將其格式化為十進位值，您需要使用 "D" 標準格式規範；若要將其格式化為十六進位值，您需要使用 "X" 標準格式規範。  
  
3.  呼叫整數值的 `ToString("D").Length` 或 `ToString("X").Length` 方法，以決定未填補之數值字串的長度。  
  
4.  將您想要包含在格式化字串中的前置零個數，加入至未填補之數值字串的長度。 這會定義填補字串的總長度。  
  
5.  呼叫整數值的 `ToString(String)` 方法，針對十進位字串，請傳遞字串 "D*n*"，針對十六進位字串，請傳遞 "X*n*"，其中 *n* 代表填補字串的總長度。 您也可以在支援複合格式的方法中，使用 "D*n*" 或 "X*n*" 格式字串。  
  
 下列範例會以五個前置零填補整數值。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>以前置零將數值填補至特定長度  
  
1.  決定您想要讓數值字串表示式的小數點左邊有幾位數。 在這個總位數中包含任何前置零。  
  
2.  定義自訂數值格式字串，使用零預留位置 ("0") 來表示零的數目下限。  
  
3.  呼叫數值的 `ToString(String)` 方法，並將其傳遞至自訂格式字串。 您也可以將自訂格式字串與支援複合格式的方法搭配使用。  
  
 下列範例會使用前置零來將數個數值格式化，讓格式化數值的小數點左邊至少有 8 位數。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>以特定數目的前置零填補數值  
  
1.  決定您想要讓數值有多少個前置零。  
  
2.  決定未填補之數值字串的小數點左邊有幾位數。 若要這樣做：  
  
    1.  決定數值字串表示法是否包含小數點符號。  
  
    2.  如果包含小數點符號，則要決定小數點左邊的字元數。  
  
         -或-  
  
         如果不包含小數點符號，則要決定字串長度。  
  
3.  建立自訂格式字串，使用零預留位置 ("0")，讓每個前置零出現在字串中，並使用零預留位置或數字預留位置 ("#") 來代表預設字串中的每個數字。  
  
4.  提供自訂格式字串，以做為數值之 `ToString(String)` 方法或支援複合格式之方法的參數。  
  
 下列範例會以五個前置零填補兩個 <xref:System.Double> 值。  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a>請參閱  
 [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [Standard Numeric Format Strings](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [複合格式](../../../docs/standard/base-types/composite-formatting.md)
