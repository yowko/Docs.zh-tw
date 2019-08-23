---
title: 在 Visual Basic 中文化特性如何影響字串
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d090a6e89a470958dd323c3f249ed0658dc1cefa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955094"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>在 Visual Basic 中文化特性如何影響字串
此說明頁面會討論 Visual Basic 如何使用文化特性資訊來執行字串轉換和比較。  
  
## <a name="when-to-use-culture-specific-strings"></a>使用特定文化特性字串的時機  
 一般來說, 您應該針對呈現給使用者的所有資料使用特定文化特性字串, 並針對您應用程式的內部資料使用文化特性不變字串。  
  
 例如, 如果您的應用程式要求使用者將日期輸入為字串, 應該會預期使用者根據其文化特性來格式化字串, 而應用程式應該適當地轉換字串。 如果您的應用程式在其使用者介面中顯示該日期, 它應該會以使用者的文化特性呈現。  
  
 不過, 如果應用程式將日期上傳至中央伺服器, 它應該根據一個特定文化特性來格式化字串, 以避免在可能不同的日期格式之間產生混淆。  
  
## <a name="culture-sensitive-functions"></a>區分文化特性的函式  
 所有 Visual Basic 字串轉換函式 (除了`Str`和`Val`函數之外) 都會使用應用程式的文化特性資訊, 確保轉換和比較適用于應用程式的文化特性 (culture)使用者.  
  
 在具有不同文化特性設定的電腦上執行的應用程式中, 成功使用字串轉換函式的關鍵, 是要瞭解哪些函式使用特定的文化特性設定, 以及使用目前文化特性設定的功能。 請注意, 根據預設, 應用程式的文化特性設定會繼承自作業系統的文化特性設定。 如需詳細資訊, <xref:Microsoft.VisualBasic.Strings.Asc%2A>請<xref:Microsoft.VisualBasic.Strings.AscW%2A>參閱<xref:Microsoft.VisualBasic.Strings.Chr%2A>、 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>、 <xref:Microsoft.VisualBasic.Strings.Format%2A>、 <xref:Microsoft.VisualBasic.Conversion.Hex%2A> 、<xref:Microsoft.VisualBasic.Conversion.Oct%2A>、、和[類型轉換](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)函式。  
  
 在字串和數位之間進行轉換時`Val` , (將數位轉換為字串)和(將字串轉換為數字)函數不會使用應用程式的文化特性資訊。`Str` 相反地, 它們只會將句號 (.) 辨識為有效的十進位分隔符號。 這些函式的文化特性感知雷同包括:  
  
- **使用目前文化特性的轉換。** 和函式會將數位轉換成字串, `CDbl`而和`CInt`函式會將字串轉換成數位。 `Format` `CStr`  
  
- **使用特定文化特性的轉換。** 每個數位物件都`ToString(IFormatProvider)`有一個方法, 可將數位轉換成字串, `Parse(String, IFormatProvider)`以及將字串轉換成數位的方法。 例如, `Double`類型會<xref:System.Double.ToString%28System.IFormatProvider%29>提供和<xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>方法。  
  
 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Conversion.Str%2A> 與 <xref:Microsoft.VisualBasic.Conversion.Val%2A>。  
  
## <a name="using-a-specific-culture"></a>使用特定文化特性  
 假設您正在開發一個應用程式, 它會將日期 (格式化為字串) 傳送至 Web 服務。 在此情況下, 您的應用程式必須使用特定的文化特性來進行字串轉換。 為了說明原因, 請考慮使用日期<xref:System.DateTime.ToString>之方法的結果:如果您的應用程式使用該方法將日期格式化為2005年7月4日, 則會在以美國英文 (en-us) 文化特性執行時傳回「7/4/2005 12:00:00 AM」, 但當以德文 (de) 文化特性執行時, 它會傳回 "04.07.2005 00:00:00"。  
  
 當您需要以特定的文化特性格式來執行字串轉換時, 您應該使用`CultureInfo`內建在 .NET Framework 中的類別。 您可以藉由將`CultureInfo`文化特性的名稱傳遞<xref:System.Globalization.CultureInfo.%23ctor%2A>至函式, 為特定文化特性建立新的物件。 支援的文化特性名稱會列在<xref:System.Globalization.CultureInfo> [類別說明] 頁面中。  
  
 或者, 您也可以從<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>屬性取得不因*文化*特性而異的實例。 不因文化特性而異是以英文文化特性為基礎, 但有一些差異。 例如, 不因文化特性而異, 會指定24小時制, 而不是12小時制的時鐘。  
  
 若要將日期轉換成文化特性的字串, 請<xref:System.Globalization.CultureInfo>將物件傳遞至 date 物件<xref:System.DateTime.ToString%28System.IFormatProvider%29>的方法。 例如, 下列程式碼會顯示 "07/04/2005 00:00:00", 不論應用程式的文化特性設定為何。  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
> 日期常值一律會根據英文文化特性來轉譯。  
  
## <a name="comparing-strings"></a>比較字串  
 需要字串比較的兩個重要情況如下:  
  
- **排序資料以顯示給使用者。** 使用以目前文化特性為基礎的作業, 以便適當地排序字串。  
  
- **判斷兩個應用程式內部字串是否完全相符 (通常是為了安全起見)。** 使用忽略目前文化特性的作業。  
  
 您可以使用 Visual Basic <xref:Microsoft.VisualBasic.Strings.StrComp%2A>函數來執行這兩種類型的比較。 指定選擇性`Compare`引數以控制比較的類型: `Text`適用于用於判斷完全相符`Binary`專案的大部分輸入和輸出。  
  
 `StrComp`函式會傳回整數, 指出兩個以排序次序為基礎的比較字串之間的關聯性。 結果的正數值表示第一個字串大於第二個字串。 負的結果表示第一個字串較小, 而零表示字串之間是否相等。  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 您也可以使用函式的 .NET Framework 夥伴`StrComp` <xref:System.String.Compare%2A?displayProperty=nameWithType> (方法)。 這是基底字串類別的靜態、多載方法。 下列範例說明如何使用此方法:  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 若要更精確地控制比較的執行方式, 您可以使用<xref:System.String.Compare%2A>方法的其他多載。 使用方法時, 您可以`comparisonType`使用引數來指定要使用的比較類型。 <xref:System.String.Compare%2A?displayProperty=nameWithType>  
  
|引數`comparisonType`的值|比較的類型|使用時機|  
|---|---|---|  
|`Ordinal`|根據字串的元件位元組進行比較。|比較時, 請使用此值: 區分大小寫的識別碼、安全性相關設定, 或位元組必須完全相符的其他非語言識別項。|  
|`OrdinalIgnoreCase`|根據字串的元件位元組進行比較。<br /><br /> `OrdinalIgnoreCase`會使用不因文化特性而異的資訊, 來判斷兩個字元只有大小寫不同。|比較時, 請使用此值: 不區分大小寫的識別碼、安全性相關設定, 以及儲存在 Windows 中的資料。|  
|`CurrentCulture` 或 `CurrentCultureIgnoreCase`|根據目前文化特性中的字串轉譯而進行的比較。|比較時, 請使用這些值: 向使用者顯示的資料、大部分的使用者輸入, 以及其他需要語言轉譯的資料。|  
|`InvariantCulture` 或 `InvariantCultureIgnoreCase`|根據字串在不因文化特性而異的轉譯而進行的比較。<br /><br /> 這與`Ordinal`和`OrdinalIgnoreCase`不同, 因為不因文化特性而異, 會將其接受範圍以外的字元視為對等的不變字元。|只有在比較保存資料或顯示需要固定排序次序的語言相關資料時, 才使用這些值。|  
  
### <a name="security-considerations"></a>安全性考量  
 如果您的應用程式根據比較或大小寫變更作業的結果來做出安全性決策, 則作業<xref:System.String.Compare%2A?displayProperty=nameWithType>應該使用方法, 並針對`comparisonType`引數`Ordinal`傳遞`OrdinalIgnoreCase`或。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Globalization.CultureInfo>
- [Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
