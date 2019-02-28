---
title: 在 Visual Basic 中文化特性如何影響字串
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: b9e9b4e199e4504e21b365706ea60d63c9d5fb87
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980941"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>在 Visual Basic 中文化特性如何影響字串
此說明頁面討論 Visual Basic 來執行字串轉換及比較所使用的文化特性資訊。  
  
## <a name="when-to-use-culture-specific-strings"></a>何時使用特定文化特性的字串  
 一般而言，您應該使用特定文化特性的字串顯示的所有資料和讀取使用者，和用於您的應用程式的內部資料的文化特性而異的字串。  
  
 比方說，如果您的應用程式會要求使用者輸入日期做為字串，它會預期要格式化的字串，其文化特性，根據使用者和應用程式應該適當地轉換字串。 如果您的應用程式接著會顯示該日期在其使用者介面中的，它應該在使用者的文化特性中呈現它。  
  
 不過，如果應用程式會將日期上傳到中央伺服器，它應該格式根據某一特定的文化特性，為了避免混淆之間可能位在不同的日期格式字串。  
  
## <a name="culture-sensitive-functions"></a>區分文化特性函式  
 所有 Visual Basic 字串轉換函式 (除了`Str`和`Val`函式) 使用應用程式的文化特性資訊，請確定轉換和比較是適用於應用程式的文化特性使用者。  
  
 若要順利使用不同的文化特性設定的電腦執行的應用程式中使用字串轉換函式的索引鍵是了解哪些函式會使用特定文化特性設定，並使用目前的文化特性設定。 請注意，應用程式的文化特性設定，根據預設，繼承自作業系統的文化特性設定。 如需詳細資訊，請參閱 < <xref:Microsoft.VisualBasic.Strings.Asc%2A>， <xref:Microsoft.VisualBasic.Strings.AscW%2A>， <xref:Microsoft.VisualBasic.Strings.Chr%2A>， <xref:Microsoft.VisualBasic.Strings.ChrW%2A>， <xref:Microsoft.VisualBasic.Strings.Format%2A>， <xref:Microsoft.VisualBasic.Conversion.Hex%2A>， <xref:Microsoft.VisualBasic.Conversion.Oct%2A>，並[類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 `Str` （將數字轉換為字串） 和`Val`（將數字字串） 函式不會使用應用程式的文化特性資訊字串和數字之間轉換時。 相反地，它們只是句號 （.） 辨識為有效的十進位分隔符號。 這些函式的文化特性感知的雷同如下：  
  
-   **使用目前文化特性的轉換。** `CStr`並`Format`函式會將數字轉換為字串，而`CDbl`和`CInt`函式會將字串轉換為數字。  
  
-   **使用特定文化特性的轉換。** 每個物件具有`ToString(IFormatProvider)`方法，將數字轉換為字串，和`Parse(String, IFormatProvider)`將字串轉換為數字的方法。 例如，`Double`型別會提供<xref:System.Double.ToString%28System.IFormatProvider%29>和<xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>方法。  
  
 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Conversion.Str%2A> 與 <xref:Microsoft.VisualBasic.Conversion.Val%2A>。  
  
## <a name="using-a-specific-culture"></a>使用特定文化特性  
 假設您正在開發的應用程式，傳送至 Web 服務的日期 （格式為字串）。 在此情況下，您的應用程式必須使用特定文化特性的字串轉換。 為了說明原因，請考慮使用的日期的結果<xref:System.DateTime.ToString>方法：如果您的應用程式會使用該方法來格式化日期 2005 年 7 月 4 日，它會傳回"2005 年 7 月 4 日上午 12:00:00"時執行的美式英文 (EN-US) 文化特性，但它會傳回"04.07.2005 00:00:00"當執行與德文 (DE-DE) 文化特性。  
  
 當您需要執行的特定文化特性格式的字串轉換時，您應該使用`CultureInfo`類別的內建[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。 您可以建立新`CultureInfo`藉由傳遞文化特性的名稱，以特定文化特性的物件<xref:System.Globalization.CultureInfo.%23ctor%2A>建構函式。 支援的文化特性名稱會列在<xref:System.Globalization.CultureInfo>類別 [說明] 頁面。  
  
 或者，您可以在其中取得的執行個體*文化特性而異*從<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>屬性。 而異的文化特性為基礎的英文文化特性，但有一些差異。 比方說，而異的文化特性會指定 24 小時制時鐘，而不是 12 小時制。  
  
 若要將日期轉換成文化特性的字串，傳遞<xref:System.Globalization.CultureInfo>日期物件的物件<xref:System.DateTime.ToString%28System.IFormatProvider%29>方法。 例如，下列程式碼會顯示 「 07/04/2005年 00:00:00"，而不論應用程式的文化特性設定。  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
>  日期常值一律會根據英文的文化特性的方式解譯。  
  
## <a name="comparing-strings"></a>比較字串  
 有兩個重要的情況下，會在所需字串比較：  
  
-   **排序資料以供顯示給使用者。** 使用根據目前文化特性，因此能適當地排序字串的作業。  
  
-   **決定是否兩個應用程式內部的字串完全符合 （通常是基於安全性目的）。** 使用忽略目前的文化特性的作業。  
  
 您可以執行使用 Visual Basic 比較這兩種<xref:Microsoft.VisualBasic.Strings.StrComp%2A>函式。 指定選擇性`Compare`控制項的比較類型的引數：`Text`適用於大部分的輸入和輸出`Binary`判斷完全相符項目。  
  
 `StrComp`函式會傳回一個整數，表示排序順序為基礎的比較兩個字串之間的關聯性。 結果為正值表示第一個字串大於第二個字串。 否定的結果指出的第一個字串為較小，而零表示字串之間的等號比較。  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 您也可以使用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]夥伴`StrComp`函式，<xref:System.String.Compare%2A?displayProperty=nameWithType>方法。 這是靜態的多載方法的基底的 string 類別。 下列範例說明如何使用這個方法：  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 更精細地控制如何執行比較的詳細資訊，您可以使用其他多載<xref:System.String.Compare%2A>方法。 具有<xref:System.String.Compare%2A?displayProperty=nameWithType>方法，您可以使用`comparisonType`引數來指定要使用的比較類型。  
  
|值`comparisonType`引數|比較類型|使用時機|  
|---|---|---|  
|`Ordinal`|根據字串的元件位元組的比較。|使用此值，比較時： 區分大小寫的識別項、 安全性相關設定或其他位元組必須完全相符的非語言識別項。|  
|`OrdinalIgnoreCase`|根據字串的元件位元組的比較。<br /><br /> `OrdinalIgnoreCase` 若要判斷兩個字元的差別只在於大小寫時，會使用而異的文化特性資訊。|使用此值，比較時： 不區分大小寫的識別項、 安全性相關設定，並儲存在 Windows 中的資料。|  
|`CurrentCulture` 或 `CurrentCultureIgnoreCase`|在目前的文化特性的字串解譯為基礎的比較。|在比較時使用這些值： 資料顯示給使用者，大部分使用者輸入，以及其他需要語言解譯的資料。|  
|`InvariantCulture` 或 `InvariantCultureIgnoreCase`|在 文化特性而異的字串解譯為基礎的比較。<br /><br /> 這是與不同`Ordinal`和`OrdinalIgnoreCase`，因為而異的文化特性會將其可接受的範圍之外的字元視為對等的非變異字元。|只比較持續資料或顯示的語言相關資料時，需要固定的排序次序，請使用這些值。|  
  
### <a name="security-considerations"></a>安全性考量  
 如果您的應用程式進行比較或大小寫變更作業的結果為基礎的安全性決策，則作業應該使用<xref:System.String.Compare%2A?displayProperty=nameWithType>方法，然後傳遞`Ordinal`或是`OrdinalIgnoreCase`如`comparisonType`引數。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Globalization.CultureInfo>
- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
