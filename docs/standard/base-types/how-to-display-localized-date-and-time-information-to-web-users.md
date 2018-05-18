---
title: 如何：對 Web 使用者顯示當地語系化的日期和時間資訊
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63775d48ca2e11cfa121f3b7aeaff708d86e50de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>如何：對 Web 使用者顯示當地語系化的日期和時間資訊
由於網頁可在世界的任何一個角落顯示，負責剖析及格式化日期和時間值的作業在與使用者互動時，並不應該仰賴單一的預設格式 (這通常是網頁伺服器當地文化特性的格式)。 相反地，處理來自使用者之日期和時間字串輸入的 Web 表單，應該使用該使用者慣用的文化特性對字串進行剖析。 同樣地，日期和時間資料應該以符合使用者文化特性的格式向該使用者顯示。 本主題顯示如何執行此動作。  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>剖析來自使用者的日期和時間字串  
  
1.  判斷是否已填入由 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 屬性所傳回的字串陣列。 如果不要，請繼續進行步驟 6。  
  
2.  如果由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列已填入，請擷取它的第一個元素。 第一個元素代表使用者預設或慣用的語言和地區。  
  
3.  藉由呼叫 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來將代表使用者慣用文化特性的 <xref:System.Globalization.CultureInfo> 物件具現化。  
  
4.  呼叫 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 類型的 `TryParse` 或 `Parse` 方法來嘗試轉換。 搭配 `provider` 參數使用 `TryParse` 或 `Parse` 方法的多載，然後將下列任一項傳遞給它：  
  
    -   在步驟 3 中建立的 <xref:System.Globalization.CultureInfo> 物件。  
  
    -   由步驟 3 中所建立 <xref:System.Globalization.CultureInfo> 物件之 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> 屬性所傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件。  
  
5.  如果轉換失敗，請針對由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回之字串陣列中的每個剩餘元素，重複執行步驟 2 到 4。  
  
6.  如果轉換仍然失敗，或由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列是空的，請使用不因文化特性而異的方式來剖析字串，這是由 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性所傳回。  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>剖析使用者要求的當地日期和時間  
  
1.  新增 <xref:System.Web.UI.WebControls.HiddenField> 控制項至 Web 表單。  
  
2.  透過將目前的日期和時間，以及當地時區針對國際標準時間 (UTC) 的時差寫入至 <xref:System.Web.UI.WebControls.HiddenField.Value%2A> 函式，來建立能處理 `Submit` 按鈕之 `onClick` 事件的 JavaScript 函式。 使用分隔符號 (例如分號) 來區分字串的兩個元件。  
  
3.  使用 Web 表單的 <xref:System.Web.UI.Control.PreRender> 事件，來透過將指令碼的文字傳遞至 <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>方法，把函式插入至 HTML 輸出資料流。  
  
4.  藉由將 JavaScript 函式的名稱提供給 `Submit` 按鈕的 `OnClientClick` 屬性，來將事件處理常式連線至 `Submit` 按鈕的 `onClick` 事件。  
  
5.  針對 `Submit` 按鈕的 <xref:System.Web.UI.WebControls.Button.Click> 事件建立處理常式。  
  
6.  在事件處理常式中，判斷是否已填入由 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 屬性所傳回的字串陣列。 如果未填入，請繼續進行步驟 14。  
  
7.  如果由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列已填入，請擷取它的第一個元素。 第一個元素代表使用者預設或慣用的語言和地區。  
  
8.  藉由呼叫 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來將代表使用者慣用文化特性的 <xref:System.Globalization.CultureInfo> 物件具現化。  
  
9. 將指派給 <xref:System.Web.UI.WebControls.HiddenField.Value%2A> 屬性的字串傳遞至 <xref:System.String.Split%2A> 方法，以將代表使用者當地日期和時間及使用者當地時區時差的字串，儲存在個別的陣列元素中。  
  
10. 呼叫 <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 或 <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> 方法，以將使用者要求的日期和時間轉換為 <xref:System.DateTime> 值。 搭配 `provider` 參數使用方法的多載，然後將下列任一項傳遞給它：  
  
    -   在步驟 8 中建立的 <xref:System.Globalization.CultureInfo> 物件。  
  
    -   由步驟 8 中所建立之 <xref:System.Globalization.CultureInfo> 物件的 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> 屬性所傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件。  
  
11. 若步驟 10 中的剖析作業失敗，請移至步驟 13。 否則，請呼叫 <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> 方法以將代表使用者時區時差的字串轉換為整數。  
  
12. 藉由呼叫 <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType> 建構函式，來具現化代表使用者當地時間的 <xref:System.DateTimeOffset>。  
  
13. 如果步驟 10 的轉換失敗，請針對由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回之字串陣列中的每個剩餘元素，重複執行步驟 7 到 12。  
  
14. 如果轉換仍然失敗，或由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列是空的，請使用不因文化特性而異的方式來剖析字串，這是由 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性所傳回。 然後重複步驟 7 到 12。  
  
 結果會產生代表您網站使用者之當地時間的 <xref:System.DateTimeOffset> 物件。 您接著可以透過呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A> 方法來判斷相對應的 UTC。 您也可以透過呼叫 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> 方法並將 <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> 的值傳遞為要轉換時間的時區，來決定您網頁伺服器上的相對應日期和時間。  
  
## <a name="example"></a>範例  
 下列範例包含會要求使用者輸入日期和時間值的 HTML 原始檔及 ASP.NET Web 表單程式碼。 用戶端指令碼也會將有關使用者要求之當地日期和時間的資訊，以及使用者相對於 UTC 的時區時差寫入隱藏的欄位。 此資訊接著會由伺服器剖析，並傳回會顯示使用者輸入的網路伺服器。 它也會使用使用者的當地時間、伺服器上的時間，以及 UTC 來顯示使用者要求的日期和時間。  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 用戶端指令碼會呼叫 JavaScript `toLocaleString` 方法。 這會產生遵循使用者地區設定之格式設定慣例的字串，這樣的字串會更容易在伺服器上成功剖析。  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 屬性會從 HTTP 要求所含之 `Accept-Language` 標頭內含的文化特性名稱來填入。 不過，並非所有瀏覽器都會在其要求中包含 `Accept-Language` 標頭，而使用者也可以完全抑制標頭。 這在剖析使用者輸入時，會使得具備後援文化特性變得很重要。 一般而言，後援文化特性是由 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 所傳回之不因文化特性而異的文化特性。 使用者也可以在文字方塊中輸入文化特性名稱以提供給 Internet Explorer，但這可能會導致文化特性名稱無效。 如此一來，將 <xref:System.Globalization.CultureInfo> 物件具現化時，使用例外狀況處理就變得很重要。  
  
 從 Internet Explorer 提交的 HTTP 要求中進行擷取時，會依照使用者喜好設定順序填入 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>。 陣列中的第一個元素會包含使用者主要文化特性/地區的名稱。 如果陣列包含任何其他項目，Internet Explorer 就會為它們任意指派一個品質指定名稱，以分號分隔文化特性名稱。 例如，適用於 fr-FR 文化特性的項目可能採取 `fr-FR;q=0.7` 的形式。  
  
 範例會搭配已設定為 `false` 的 `useUserOverride` 參數呼叫 <xref:System.Globalization.CultureInfo.%23ctor%2A> 建構函式，以建立新的 <xref:System.Globalization.CultureInfo> 物件。 這可確保在文化特性名稱為伺服器預設文化特性名稱的情況下，由類別建構函式所建立的新 <xref:System.Globalization.CultureInfo> 物件就會包含文化特性的預設設定，而且不會反映使用伺服器的**地區及語言選項**應用程式所覆寫的任何設定。 來自伺服器上任何已覆寫設定的值可能不存在於使用者的系統上或反映於使用者的輸入中。  
  
 由於此範例會剖析兩個代表日期和時間的字串 (一個為使用者輸入，另一個則儲存至隱藏欄位)，它會預先定義可能會用到的 <xref:System.Globalization.CultureInfo> 物件。 它會建立 <xref:System.Globalization.CultureInfo> 物件的陣列，其數目會比由 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 屬性所傳的元素數目還要多上一個。 接著它會針對每個語言/地區字串具現化 <xref:System.Globalization.CultureInfo> 物件，同時也會具現化代表 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>的 <xref:System.Globalization.CultureInfo> 物件。  
  
 您的程式碼可以呼叫 <xref:System.DateTime.Parse%2A> 或 <xref:System.DateTime.TryParse%2A> 方法，以將使用者代表日期和時間的字串轉換為 <xref:System.DateTime> 值。 您可能需要針對單一剖析作業重複呼叫剖析方法。 因此，<xref:System.DateTime.TryParse%2A> 方法是一個較佳的作法，因為它會在剖析作業失敗時傳回 `false`。 相反地，在 Web 應用程式中處理 <xref:System.DateTime.Parse%2A> 方法可能擲回的重複例外狀況，是個非常耗費成本的作法。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，請在不搭配程式碼後置的情況下建立 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網頁。 然後將範例複製到網頁中，以它取代所有現有的程式碼。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網頁應包含下列控制項：  
  
-   <xref:System.Web.UI.WebControls.Label> 控制項，程式碼中並未參考此控制項。 將它的 <xref:System.Web.UI.WebControls.TextBox.Text%2A> 屬性設定為 "Enter a Number:"。  
  
-   名為 `DateString` 的 <xref:System.Web.UI.WebControls.TextBox> 控制項。  
  
-   名為 `OKButton` 的 <xref:System.Web.UI.WebControls.Button> 控制項。 將它的 <xref:System.Web.UI.WebControls.Button.Text%2A> 屬性設為 "OK"。  
  
-   名為 `DateInfo` 的 <xref:System.Web.UI.WebControls.HiddenField> 控制項。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 為了防止使用者將指令碼插入至 HTML 資料流，絕對不應在伺服器回應中直接回應使用者輸入。 而應改用 <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> 方法進行編碼。  
  
## <a name="see-also"></a>請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [剖析日期和時間字串](../../../docs/standard/base-types/parsing-datetime.md)
