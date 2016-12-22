---
title: "How Culture Affects Strings in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "locale, effect on strings"
  - "strings [Visual Basic], locale dependence"
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How Culture Affects Strings in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

本說明網頁會討論 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 如何使用文化特性資訊，執行字串轉換和比較。  
  
## 何時使用因文化特性而異的字串  
 通常，您應該對所有呈現給使用者和從使用者讀取的資料使用因文化特性而異的字串，並且對應用程式的內部資料使用不因文化特性而異的字串。  
  
 例如，如果應用程式要求使用者將日期輸入為字串，則它會預期使用者根據文化特性將字串格式化，而且應用程式會適當地轉換字串。  如果應用程式之後在使用者介面中呈現該日期，則應該以使用者的文化特性加以呈現。  
  
 然而，如果應用程式將日期上載到中央伺服器，則它應該根據某個特定文化特性將字串格式化，以免在可能不同的日期格式之間產生混淆。  
  
## 區分文化特性的函式  
 所有 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 字串轉換函式 \(`Str` 和 `Val` 函式除外\) 都會使用應用程式的文化特性資訊，確定轉換與比較工作適合於應用程式使用者的文化特性。  
  
 要在具有不同文化特性設定之電腦上執行的應用程式中順利地使用字串轉換函式，關鍵在於了解哪些函式使用特定的文化特性設定，以及哪些函式使用目前的文化特性設定。  請注意，應用程式的文化特性設定依預設是繼承自作業系統的文化特性設定。  如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Strings.Asc%2A>、<xref:Microsoft.VisualBasic.Strings.AscW%2A>、<xref:Microsoft.VisualBasic.Strings.Chr%2A>、<xref:Microsoft.VisualBasic.Strings.ChrW%2A>、<xref:Microsoft.VisualBasic.Strings.Format%2A>、<xref:Microsoft.VisualBasic.Conversion.Hex%2A>、<xref:Microsoft.VisualBasic.Conversion.Oct%2A> 和[Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 在字串與數字之間進行轉換時，`Str` \(將數字轉換為字串\) 和 `Val` \(將字串轉換為數字\) 函式不會使用應用程式的文化特性資訊，  只會將句號 \(.\) 辨識為有效的小數分隔符號。  這些函式的文化特性感知的類似情況如下：  
  
-   **使用目前文化特性的轉換** ：`CStr` 和 `Format` 函式會將數字轉換為字串，而 `CDbl` 和 `CInt` 函式則會將字串轉換為數字。  
  
-   **使用特定文化特性的轉換** ：每一個數字物件都有會將數字轉換為字串的 `ToString(IFormatProvider)` 方法，以及會將字串轉換為數字的 `Parse(String, IFormatProvider)` 方法。  例如，`Double` 型別會提供 <xref:System.Double.ToString%28System.IFormatProvider%29> 和 <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> 方法。  
  
 如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.Conversion.Str%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Val%2A>。  
  
## 使用特定文化特性  
 想像您正在開發一個會將日期 \(格式化為字串\) 傳送至 Web 服務的應用程式。  在此情況下，您的應用程式必須使用特定文化特性，進行字串轉換。  為了說明原因，請參考使用日期之 <xref:System.DateTime.ToString> 方法的結果：如果應用程式使用該方法格式化日期 2005 年 7 月 4 日，則以美式英文 \(en\-US\) 文化特性執行時會傳回 "7\/4\/2005 12:00:00 AM"，但是以德文 \(de\-DE\) 文化特性執行時則會傳回 "04.07.2005 00:00:00"。  
  
 當您需要以特定文化特性格式執行字串轉換時，您應該使用 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 內建的 `CultureInfo` 類別。  您可以將文化特性的名稱傳遞至 <xref:System.Globalization.CultureInfo.%23ctor%2A> 建構函式 \(Constructor\)，為特定文化特性建立新的 `CultureInfo` 物件。  支援的文化特性名稱會列在 <xref:System.Globalization.CultureInfo> 類別說明網頁中。  
  
 此外，您可以從 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 屬性取得「*不因文化特性而異*」\(Invariant Culture\) 的執行個體。  不因文化特性而異是以「英文」文化特性為準，但有一些差異。  例如，不因文化特性而異指定的是 24 小時制，不是 12 小時制。  
  
 若要將日期轉換為文化特性的字串，請將 <xref:System.Globalization.CultureInfo> 物件傳遞至日期物件的 <xref:System.DateTime.ToString%28System.IFormatProvider%29> 方法。  例如，不論應用程式的文化特性設定為何，下列程式碼都會顯示為 "07\/04\/2005 00:00:00"。  
  
 [!code-vb[VbVbalrConcepts#1](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  日期常值 \(Literal\) 一律會根據英文文化特性解譯。  
  
## 比較字串  
 需要字串比較的重要情況有兩種：  
  
-   **將要顯示給使用者的資料排序。** 使用以目前文化特性為基礎的作業，以便字串能適當地排序。  
  
-   **判斷兩個應用程式內部的字串是否完全相符 \(通常基於安全目的\)。** 使用不受目前文化特性影響的作業。  
  
 您可以使用 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Strings.StrComp%2A> 函式執行這兩種比較。  指定選擇性的 `Compare` 引數就可以控制比較類型：`Text` 用於大部分輸入和輸出，`Binary` 用於判斷完全相符。  
  
 `StrComp` 函式會傳回一個整數，指出根據排序順序比較的兩個字串之間有何關聯性。  結果為正數表示第一個字串大於第二個字串。  負數結果則表示第一個字串較小，零表示兩個字串相等。  
  
 [!code-vb[VbVbalrStrings#22](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 您也可以使用 `StrComp` 函式的 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] 夥伴 \(<xref:System.String.Compare%2A?displayProperty=fullName> 方法\)。  這是個靜態 \(Static\)、多載的基底字串類別方法。  下列範例示範如何使用此方法：  
  
 [!code-vb[VbVbalrStrings#48](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 如需更精細地控制如何執行比較，您可以使用 <xref:System.String.Compare%2A> 方法的其他多載。  利用 <xref:System.String.Compare%2A?displayProperty=fullName> 方法，您可以使用 `comparisonType` 引數，指定要使用哪種比較方式。  
  
||||  
|-|-|-|  
|`comparisonType` 引數的值|比較類型|使用時機|  
|`Ordinal`|以字串的元件位元組為基礎的比較。|在比較下列項目時使用此值：區分大小寫的識別項、安全性相關設定，或位元組必須完全相符的其他非語言識別項。|  
|`OrdinalIgnoreCase`|以字串的元件位元組為基礎的比較。<br /><br /> 當兩個字元只有大小寫不同時，`OrdinalIgnoreCase` 會使用不因文化特性而異的資訊進行判斷。|在比較下列項目時使用此值：不區分大小寫的識別項、安全性相關設定，以及 Windows 中儲存的資料。|  
|`CurrentCulture` 或 `CurrentCultureIgnoreCase`|以目前文化特性中的字串解譯為基礎的比較。|在比較下列項目時使用這些值：顯示給使用者的資料、大部分使用者的輸入，以及其他需要語言解譯的資料。|  
|`InvariantCulture` 或 `InvariantCultureIgnoreCase`|以不因文化特性而異的字串解譯為基礎的比較。<br /><br /> 因為不因文化特性而異會將超出其接受範圍的字元視為相等的不變字元，所以這不同於 `Ordinal` 和 `OrdinalIgnoreCase`。|只在比較持續資料或顯示需要固定排序次序的語言相關資料時，才使用這些值。|  
  
### 安全性考量  
 如果應用程式會根據比較或大小寫變更作業的結果，做出安全性決策，則作業應該會使用 <xref:System.String.Compare%2A?displayProperty=fullName> 方法，並且傳遞 `comparisonType` 引數的 `Ordinal` 或 `OrdinalIgnoreCase`。  
  
## 請參閱  
 <xref:System.Globalization.CultureInfo>   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)