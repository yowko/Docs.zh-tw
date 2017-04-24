---
title: "如何：對 Web 使用者顯示當地語系化的日期和時間資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "顯示日期和時間資料"
  - "格式化 [.NET Framework], 日期"
  - "格式化 [.NET Framework], 當地語系化資料"
  - "當地語系化 [.NET Framework], 日期和時間顯示"
  - "當地語系化日期顯示 [.NET Framework]"
  - "剖析字串 [.NET Framework], 日期和時間字串"
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：對 Web 使用者顯示當地語系化的日期和時間資訊
由於網頁可在任何地方顯示，因此與使用者互動時，剖析和格式化日期與時間值的作業不應倚賴預設格式 \(大部分情況下為 Web 伺服器上本機文化特性的格式\)。  處理使用者輸入之日期和時間字串的 Web Form 應改用使用者偏好的文化特性剖析字串。  同樣地，對使用者顯示的日期和時間資料應使用符合使用者文化特性的格式。  本主題將說明如何執行這項作業。  
  
### 剖析使用者輸入的日期和時間字串  
  
1.  判斷 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 屬性傳回的字串陣列是否已填入。  如果尚未填入，則繼續進行步驟 6。  
  
2.  如果 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列已填入，就會擷取它的第一個項目。  第一個項目指出使用者的預設或慣用的語言和區域。  
  
3.  呼叫 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName> 建構函式以具現化 <xref:System.Globalization.CultureInfo> 物件，此物件代表使用者慣用的文化特性。  
  
4.  呼叫 <xref:System.DateTime> 或 <xref:System.DateTimeOffset> 型別的 `TryParse` 或 `Parse` 方法嘗試轉換。  使用 `TryParse` 或 `Parse` 方法的多載與 `provider` 參數，並將下列任一項傳遞給該多載：  
  
    -   在步驟 3 中建立的 <xref:System.Globalization.CultureInfo> 物件。  
  
    -   在步驟 3 中所建立 <xref:System.Globalization.CultureInfo> 物件的 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> 屬性傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件。  
  
5.  如果轉換失敗，則針對 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性傳回的字串陣列中其餘每一個項目重複步驟 2 到 4。  
  
6.  如果轉換還是失敗，或者，如果 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列為空白，請使用由 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 屬性所傳回的 Invariant 文化特性 \(不因文化特定而異\) 來剖析字串。  
  
### 剖析使用者要求的本地日期和時間  
  
1.  在 Web Form 中加入 <xref:System.Web.UI.WebControls.HiddenField> 控制項。  
  
2.  建立 JavaScript 函式，該函式會將目前的日期和時間以及本機時區與 Coordinated Universal Time \(UTC\) 之間的位移寫入 <xref:System.Web.UI.WebControls.HiddenField.Value%2A> 屬性，藉此處理 `Submit` 按鈕的 `onClick` 事件。  使用分隔符號 \(例如分號\) 分隔字串的兩個元件。  
  
3.  將指令碼的文字傳遞至 <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=fullName> 方法，藉此使用 Web Form 的 <xref:System.Web.UI.Control.PreRender> 事件將函式插入 HTML 輸出資料流中。  
  
4.  藉由提供 JavaScript 函式的名稱給 `Submit` 按鈕的 `OnClientClick` 屬性，連接事件處理常式與 `Submit` 按鈕的 `onClick` 事件。  
  
5.  為 `Submit` 按鈕的 <xref:System.Web.UI.WebControls.Button.Click> 事件建立處理常式。  
  
6.  判斷 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 屬性傳回的字串陣列是否已填入事件處理常式中。  如果尚未填入，則繼續進行步驟 14。  
  
7.  如果 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列已填入，就會擷取它的第一個項目。  第一個項目指出使用者的預設或慣用的語言和區域。  
  
8.  呼叫 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName> 建構函式以具現化 <xref:System.Globalization.CultureInfo> 物件，此物件代表使用者慣用的文化特性。  
  
9. 將指派給 <xref:System.Web.UI.WebControls.HiddenField.Value%2A> 屬性的字串傳遞至 <xref:System.String.Split%2A> 方法，藉此將使用者本地日期和時間的字串表示，以及使用者本機時區位移的字串表示儲存到不同的陣列項目中。  
  
10. 呼叫 <xref:System.DateTime.Parse%2A?displayProperty=fullName> 或 <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=fullName> 方法，將使用者要求的日期和時間轉換成 <xref:System.DateTime> 值。  使用方法多載與 `provider` 參數，並將下列任一項傳遞給該多載：  
  
    -   在步驟 8 中建立的 <xref:System.Globalization.CultureInfo> 物件。  
  
    -   在步驟 8 中所建立 <xref:System.Globalization.CultureInfo> 物件的 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> 屬性傳回的 <xref:System.Globalization.DateTimeFormatInfo> 物件。  
  
11. 如果步驟 10 中的剖析作業失敗，請移至步驟 13。  否則，請呼叫 <xref:System.UInt32.Parse%28System.String%29?displayProperty=fullName> 方法，將使用者時區位移的字串表示轉換成整數。  
  
12. 具現化 <xref:System.DateTimeOffset>，它會藉由呼叫 <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=fullName> 建構函式的方式呈現使用者的本機時間。  
  
13. 如果步驟 10 中的轉換失敗，則針對 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性傳回的字串陣列中其餘每一個項目重複步驟 7 到 12。  
  
14. 如果轉換還是失敗，或者，如果 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列為空白，請使用由 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 屬性所傳回的 Invariant 文化特性 \(不因文化特定而異\) 來剖析字串。  然後重複步驟 7 到 12。  
  
 執行結果為 <xref:System.DateTimeOffset> 物件，表示網頁使用者的本地時間。  然後您可以呼叫 <xref:System.DateTimeOffset.ToUniversalTime%2A> 方法以判斷對等的 UTC。  您也可以呼叫 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=fullName> 方法並且傳遞 <xref:System.TimeZoneInfo.Local%2A?displayProperty=fullName> 的值做為轉換時間的目標時區，藉此判斷 Web 伺服器上的對等日期和時間。  
  
## 範例  
 以下範例同時包含 HTML 原始檔和 ASP.NET Web Form 的程式碼，會要求使用者輸入日期和時間值。  用戶端指令碼也會將使用者要求的本地日期和時間資訊，以及使用者時區與 UTC 之間的位移寫入隱藏欄位中。  伺服器會接著剖析這項資訊，並傳回顯示使用者輸入的網頁。  此外還會利用使用者的本地時間、伺服器上的時間及 UTC，顯示使用者要求的日期和時間。  
  
 <!-- TODO: review snippet reference [!code-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]  -->
 <!-- TODO: review snippet reference [!code-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]  -->  
  
 用戶端指令碼會呼叫 JavaScript `toLocaleString` 方法。  如此會產生一個字串，該字串符合使用者地區設定的格式設定慣例，這可增加在伺服器上剖析該字串的成功率。  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 屬性會從 HTTP 要求所包含 `Accept-Language` 標頭中的文化特性名稱填入。  不過，並非所有瀏覽器的要求都包含 `Accept-Language` 標頭，而且使用者可以完全隱藏標頭。  因此，剖析使用者輸入時務必有後援文化特性。  通常後援文化特性是 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 傳回的不因國別而異的文化特性。  使用者也可以將文字方塊中輸入的文化特性名稱提供給 Internet Explorer，如此可能讓文化特性名稱無效。  因此具現化 <xref:System.Globalization.CultureInfo> 物件時，務必使用例外狀況處理。  
  
 從 Internet Explorer 提交的 HTTP 要求擷取時，<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 陣列會依使用者偏好設定填入。  陣列中的第一個項目包含使用者主要文化特性\/區域的名稱。  如果陣列包含任何額外的項目，Internet Explorer 會為這些項目指派任意限定規範，並且使用分號與文化特性名稱分隔。  例如，fr\-FR 文化特性的項目可能採用這個格式 `fr-FR;q=0.7`。  
  
 範例會呼叫 <xref:System.Globalization.CultureInfo.%23ctor%2A> 建構函式，且其 `useUserOverride` 參數會設為 `false`，以建立新的 <xref:System.Globalization.CultureInfo> 物件。  如此可確定，如果文化特性名稱是伺服器上預設的文化特性名稱，則類別建構函式建立的 <xref:System.Globalization.CultureInfo> 物件會包含文化特性的預設設定，並且不會反映使用伺服器的 \[**地區及語言選項**\] 應用程式覆寫的任何設定。  伺服器上任何覆寫設定的值都不會出現在使用者的系統上，或是反映在使用者輸入中。  
  
 由於這個範例會剖析兩個日期和時間的字串表示 \(一個由使用者輸入，另一個儲存到隱藏欄位\)，因此會預先定義可能需要的 <xref:System.Globalization.CultureInfo> 物件。  它會建立 <xref:System.Globalization.CultureInfo> 物件陣列，該陣列會比 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 屬性傳回的項目數大。  然後具現化每個語言\/區域字串的 <xref:System.Globalization.CultureInfo> 物件，同時還會具現化代表 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 的 <xref:System.Globalization.CultureInfo> 物件。  
  
 您的程式碼可以呼叫 <xref:System.DateTime.Parse%2A> 或 <xref:System.DateTime.TryParse%2A> 方法，將使用者的日期和時間字串表示轉換成 <xref:System.DateTime> 值。  您可能需要針對單一剖析作業重複呼叫剖析方法。  因此 <xref:System.DateTime.TryParse%2A> 方法可能較佳，因為它會在剖析作業失敗時傳回 `false`。  相反地，對於 Web 應用程式而言，處理 <xref:System.DateTime.Parse%2A> 方法可能擲回的重複例外狀況可能是相當昂貴的方法。  
  
## 編譯程式碼  
 若要編譯程式碼，請建立沒有程式碼後置 \(Code\-behind\) 的 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網頁。  然後將範例複製到網頁中，取代所有現有的程式碼。  [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網頁應包含下列控制項：  
  
-   <xref:System.Web.UI.WebControls.Label> 控制項，程式碼中並未參考這個控制項。  將 <xref:System.Web.UI.WebControls.TextBox.Text%2A> 屬性設為 \[輸入數字：\]。  
  
-   名為 `DateString` 的 <xref:System.Web.UI.WebControls.TextBox> 控制項。  
  
-   名為 `OKButton` 的 <xref:System.Web.UI.WebControls.Button> 控制項。  將 <xref:System.Web.UI.WebControls.Button.Text%2A> 屬性設為 \[確定\]。  
  
-   名為 `DateInfo` 的 <xref:System.Web.UI.WebControls.HiddenField> 控制項。  
  
## .NET Framework 安全性  
 為避免使用者將指令碼插入 HTML 資料流中，絕不可將使用者輸入直接回應 \(Echo\) 至伺服器回應中。  而是使用 <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=fullName> 方法將使用者輸入編碼。  
  
## 請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [標準日期和時間格式字串](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)   
 [自訂日期和時間格式字串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)   
 [剖析日期和時間字串](../../../docs/standard/base-types/parsing-datetime.md)