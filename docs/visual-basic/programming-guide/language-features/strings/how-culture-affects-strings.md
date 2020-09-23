---
title: 文化特性 (Culture) 如何影響字串
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: 878e028f7c7f0e93752765272e93baa3ffe1426d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059207"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>在 Visual Basic 中文化特性如何影響字串

此說明頁面會討論 Visual Basic 如何使用文化特性資訊來執行字串轉換和比較。  
  
## <a name="when-to-use-culture-specific-strings"></a>使用特定文化特性字串的時機  

 一般來說，您應該針對呈現給使用者的所有資料使用文化特性特定的字串，並針對應用程式的內部資料使用文化特性非變異字串。  
  
 例如，如果您的應用程式要求使用者將日期輸入為字串，則應該預期使用者會根據其文化特性來格式化字串，而應用程式應適當地轉換字串。 如果您的應用程式在其使用者介面中顯示該日期，它應該會以使用者的文化特性呈現。  
  
 但是，如果應用程式將日期上傳至中央伺服器，則應該根據一個特定文化特性來格式化字串，以防止可能不同的日期格式產生混淆。  
  
## <a name="culture-sensitive-functions"></a>區分文化特性的函式  

 除了和函式以外，所有 Visual Basic 字串轉換函式 (都 `Str` `Val`) 使用應用程式的文化特性資訊，以確保轉換和比較適用于應用程式使用者的文化特性。  
  
 在具有不同文化特性設定之電腦上執行的應用程式中，成功使用字串轉換函式的關鍵是瞭解哪些函式使用特定的文化特性設定，以及使用目前文化特性設定的功能。 請注意，根據預設，應用程式的文化特性設定會繼承自作業系統的文化特性設定。 如需詳細資訊，請參閱、、、、、 <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> <xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Hex%2A> 、 <xref:Microsoft.VisualBasic.Conversion.Oct%2A> 和 [類型轉換函數](../../../language-reference/functions/type-conversion-functions.md)。  
  
 `Str` (會將數位轉換為字串) ，而且 `Val` (會將字串轉換成數位) 函式在字串與數位之間轉換時，不會使用應用程式的文化特性資訊。 相反地，它們只會辨識句點 (。 ) 為有效的小數分隔符號。 這些函式的文化特性感知雷同為：  
  
- **使用目前文化特性的轉換。** 和函式會 `CStr` `Format` 將數位轉換成字串，而和函式會 `CDbl` `CInt` 將字串轉換成數位。  
  
- **使用特定文化特性的轉換。** 每個數位物件都有 `ToString(IFormatProvider)` 方法可將數位轉換成字串，以及將 `Parse(String, IFormatProvider)` 字串轉換成數位的方法。 例如，類型會 `Double` 提供 <xref:System.Double.ToString%28System.IFormatProvider%29> 和 <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> 方法。  
  
 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Conversion.Str%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Val%2A>。  
  
## <a name="using-a-specific-culture"></a>使用特定文化特性  

 假設您正在開發的應用程式會將日期 (格式化為字串) 至 Web 服務。 在此情況下，您的應用程式必須使用特定的文化特性進行字串轉換。 為了說明原因，請考慮使用日期方法的結果 <xref:System.DateTime.ToString> ：如果您的應用程式使用該方法來格式化日期2005年7月4日的日期，則會在以美國英文 (en-us) 文化特性時傳回 "7/4/2005 12:00:00 AM"，但在使用德文 (取消刪除) 文化特性時，會傳回 "04.07.2005 00:00:00"。  
  
 當您需要以特定的文化特性格式執行字串轉換時，您應該使用 `CultureInfo` .NET Framework 內建的類別。 您可以藉由將 `CultureInfo` 文化特性的名稱傳遞至函式，來為特定文化特性建立新的物件 <xref:System.Globalization.CultureInfo.%23ctor%2A> 。 支援的文化特性名稱會列在 [類別說明] <xref:System.Globalization.CultureInfo> 頁面中。  
  
 或者，您也可以從屬性取得不因 *文化* 特性而異的實例 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 。 非變異文化特性是以英文文化特性為基礎，但有一些差異。 例如，不因文化特性而異，會指定24小時制，而不是12小時制。  
  
 若要將日期轉換為文化特性的字串，請將 <xref:System.Globalization.CultureInfo> 物件傳遞給 date 物件的 <xref:System.DateTime.ToString%28System.IFormatProvider%29> 方法。 例如，下列程式碼會顯示 "07/04/2005 00:00:00"，不論應用程式的文化特性設定為何。  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> 日期常值一律會根據英文文化特性來解讀。  
  
## <a name="comparing-strings"></a>比較字串  

 有兩個重要的情況需要字串比較：  
  
- **排序要顯示給使用者的資料。** 使用以目前文化特性為基礎的作業，以便適當地排序字串。  
  
- **判斷兩個應用程式內部字串是否完全符合 (通常基於安全性目的) 。** 使用會忽略目前文化特性的作業。  
  
 您可以使用 Visual Basic 函數來執行這兩種類型的比較 <xref:Microsoft.VisualBasic.Strings.StrComp%2A> 。 指定選擇性的 `Compare` 引數來控制比較的類型： `Text` 用於判斷完全相符專案的大部分輸入和輸出 `Binary` 。  
  
 此 `StrComp` 函數會傳回一個整數，指出兩個比較的字串是否以排序次序為基礎的關聯性。 結果的正值表示第一個字串大於第二個字串。 負的結果表示第一個字串較小，而零表示字串之間是否相等。  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 您也可以使用函式的 .NET Framework 夥伴 `StrComp` （方法） <xref:System.String.Compare%2A?displayProperty=nameWithType> 。 這是基底字串類別的靜態多載方法。 下列範例說明如何使用此方法：  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 若要更精確地控制比較的執行方式，您可以使用方法的其他多載 <xref:System.String.Compare%2A> 。 利用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法，您可以使用 `comparisonType` 引數來指定要使用的比較類型。  
  
|`comparisonType`引數的值|比較的類型|使用時機|  
|---|---|---|  
|`Ordinal`|根據字串元件的位元組進行比較。|比較時，請使用此值：區分大小寫的識別碼、安全性相關設定或其他非語言識別項，其中位元組必須完全相符。|  
|`OrdinalIgnoreCase`|根據字串元件的位元組進行比較。<br /><br /> `OrdinalIgnoreCase` 使用不因文化特性而異的資訊，來判斷兩個字元的大小寫差異。|比較時，請使用此值：不區分大小寫的識別碼、安全性相關設定和儲存在 Windows 中的資料。|  
|`CurrentCulture` 或 `CurrentCultureIgnoreCase`|根據目前文化特性中字串的解讀進行比較。|比較時使用這些值：顯示給使用者的資料、大部分的使用者輸入，以及其他需要語言轉譯的資料。|  
|`InvariantCulture` 或 `InvariantCultureIgnoreCase`|以非變異文化特性中的字串轉譯為基礎的比較。<br /><br /> 這與 `Ordinal` 和不同，因為不因文化特性而異，會 `OrdinalIgnoreCase` 將其接受範圍以外的字元視為相等的非變異字元。|只有在比較保存資料或顯示需要固定排序次序的語言相關資料時，才使用這些值。|  
  
### <a name="security-considerations"></a>安全性考量  

 如果您的應用程式會根據比較或大小寫變更作業的結果做出安全性決策，則作業應該使用 <xref:System.String.Compare%2A?displayProperty=nameWithType> 方法，並傳遞 `Ordinal` 或 `OrdinalIgnoreCase` 作為 `comparisonType` 引數。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.CultureInfo>
- [Visual Basic 中的字串簡介](introduction-to-strings.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
