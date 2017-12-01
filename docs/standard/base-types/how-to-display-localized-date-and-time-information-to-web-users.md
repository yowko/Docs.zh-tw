---
title: "如何：對 Web 使用者顯示當地語系化的日期和時間資訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21493e0e0c9e42cf5efc42d86c8f126fbae9b392
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>如何：對 Web 使用者顯示當地語系化的日期和時間資訊
網頁可以顯示世界中的任何位置，因為剖析和格式化日期和時間值的作業不應依賴預設格式 （這通常是網頁伺服器的本機文化特性格式） 與使用者互動時。 相反地，Web form 處理日期和時間字串輸入，使用者應該剖析使用使用者的慣用文化特性的字串。 同樣地，日期和時間資料，應該會顯示給使用者，以符合使用者的文化特性的格式。 本主題顯示如何執行此動作。  
  
### <a name="to-parse-date-and-time-strings-input-by-the-user"></a>剖析日期和時間字串的使用者輸入  
  
1.  決定所傳回的字串陣列是否<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>屬性填入。 如果不是，繼續進行步驟 6。  
  
2.  如果傳回的字串陣列<xref:System.Web.HttpRequest.UserLanguages%2A>屬性填入，擷取其第一個元素。 第一個項目表示使用者的預設或慣用的語言和地區。  
  
3.  具現化<xref:System.Globalization.CultureInfo>物件，代表使用者的慣用文化特性，藉由呼叫<xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>建構函式。  
  
4.  呼叫`TryParse`或`Parse`方法<xref:System.DateTime>或<xref:System.DateTimeOffset>再試一次轉換的類型。 使用的多載`TryParse`或`Parse`方法`provider`參數，並將它傳遞下列任一項：  
  
    -   <xref:System.Globalization.CultureInfo>步驟 3 中建立的物件。  
  
    -   <xref:System.Globalization.DateTimeFormatInfo>所傳回的物件<xref:System.Globalization.CultureInfo.DateTimeFormat%2A>屬性<xref:System.Globalization.CultureInfo>步驟 3 中建立的物件。  
  
5.  如果轉換失敗，重複步驟 2 到 4 的字串陣列中每個剩餘的項目所傳回<xref:System.Web.HttpRequest.UserLanguages%2A>屬性。  
  
6.  如果轉換仍失敗，或傳回的字串陣列<xref:System.Web.HttpRequest.UserLanguages%2A>屬性是空的傳回使用文化特性而異，剖析字串<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>屬性。  
  
### <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>要剖析的本地日期和時間的使用者要求  
  
1.  新增<xref:System.Web.UI.WebControls.HiddenField>的 Web 表單控制項。  
  
2.  建立 JavaScript 函式會處理`onClick`事件`Submit`按鈕與國際標準時間 (UTC) 以撰寫目前的日期和時間和本機時區位移<xref:System.Web.UI.WebControls.HiddenField.Value%2A>屬性。 使用 （例如分號） 分隔符號來分隔字串的兩個元件。  
  
3.  使用 Web form<xref:System.Web.UI.Control.PreRender>事件，將函式插入至 HTML 輸出資料流傳遞到指令碼的文字<xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>方法。  
  
4.  連接的事件處理常式`Submit`按鈕的`onClick`事件提供的 JavaScript 函式名稱`OnClientClick`屬性`Submit` 按鈕。  
  
5.  建立的處理常式`Submit`按鈕的<xref:System.Web.UI.WebControls.Button.Click>事件。  
  
6.  中的事件處理常式，判斷字串陣列是否已由<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>屬性填入。 如果沒有，請繼續步驟 14。  
  
7.  如果傳回的字串陣列<xref:System.Web.HttpRequest.UserLanguages%2A>屬性填入，擷取其第一個元素。 第一個項目表示使用者的預設或慣用的語言和地區。  
  
8.  具現化<xref:System.Globalization.CultureInfo>物件，代表使用者的慣用文化特性，藉由呼叫<xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>建構函式。  
  
9. 傳遞字串指派給<xref:System.Web.UI.WebControls.HiddenField.Value%2A>屬性<xref:System.String.Split%2A>方法，以將使用者的本機日期和時間的字串表示和使用者的當地時區位移的字串表示法儲存在個別的陣列項目。  
  
10. 呼叫<xref:System.DateTime.Parse%2A?displayProperty=nameWithType>或<xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType>方法，將轉換的日期和時間的使用者要求以<xref:System.DateTime>值。 使用與方法多載`provider`參數，並將它傳遞下列任一項：  
  
    -   <xref:System.Globalization.CultureInfo>步驟 8 中建立的物件。  
  
    -   <xref:System.Globalization.DateTimeFormatInfo>所傳回的物件<xref:System.Globalization.CultureInfo.DateTimeFormat%2A>屬性<xref:System.Globalization.CultureInfo>步驟 8 中建立的物件。  
  
11. 如果在步驟 10 中的，剖析作業失敗，請移至步驟 13。 否則，呼叫<xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType>方法，將使用者的時區時差的字串表示轉換成整數。  
  
12. 具現化<xref:System.DateTimeOffset>表示藉由呼叫使用者的本機時間<xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType>建構函式。  
  
13. 如果在步驟 10 中的轉換失敗，重複步驟 7 到 12 的字串陣列中每個剩餘的項目所傳回<xref:System.Web.HttpRequest.UserLanguages%2A>屬性。  
  
14. 如果轉換仍失敗，或傳回的字串陣列<xref:System.Web.HttpRequest.UserLanguages%2A>屬性是空的傳回使用文化特性而異，剖析字串<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>屬性。 然後重複步驟 7 到 12。  
  
 結果是<xref:System.DateTimeOffset>代表當地時間之使用者的 Web 網頁的物件。 您可以藉由呼叫接著判斷相等的 UTC<xref:System.DateTimeOffset.ToUniversalTime%2A>方法。 您也可以判斷相等的日期和時間在網頁伺服器上藉由呼叫<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>方法，並將值傳遞<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>做為要轉換的時間的時區。  
  
## <a name="example"></a>範例  
 下列範例包含的 HTML 原始檔並要求使用者輸入的日期和時間值的 ASP.NET Web 表單的程式碼。 用戶端指令碼也將資訊寫入本機日期和時間的使用者要求和使用者的時區位移與 utc 之間隱藏的欄位。 這項資訊會由伺服器傳回網頁上顯示使用者的輸入剖析。 它也會顯示的日期和時間的使用者要求使用伺服器與 UTC 的使用者的本機時間的時間。  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 用戶端指令碼會呼叫 JavaScript`toLocaleString`方法。 這會產生使用者的地區設定，這可能會更容易在伺服器上成功剖析的格式設定慣例的字串。  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>中所包含的文化特性名稱填入屬性`Accept-Language`包含在 HTTP 要求標頭。 不過，並非所有瀏覽器包括`Accept-Language`標頭中的要求，以及使用者也可以抑制標頭完全。 這使得剖析使用者輸入時，必須有後援文化特性。 後援文化特性通常是所傳回的文化特性而異<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。 使用者也可以提供 Internet Explorer 具有文化特性名稱其輸入在文字方塊中，會建立文化特性名稱可能不是有效的可能性。 這使得重要具現化時使用例外狀況處理<xref:System.Globalization.CultureInfo>物件。  
  
 從 Internet Explorer 所送出的 HTTP 要求擷取時<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>陣列填入使用者的喜好順序。 陣列中的第一個項目包含使用者的主要文化特性/地區的名稱。 如果陣列包含任何其他項目，Internet Explorer 任意指派這些品質規範，以分號分隔的文化特性名稱。 例如，為 FR-FR 文化特性的項目可能會`fr-FR;q=0.7`。  
  
 範例會呼叫<xref:System.Globalization.CultureInfo.%23ctor%2A>建構函式與它`useUserOverride`參數設定為`false`來建立新的<xref:System.Globalization.CultureInfo>物件。 如此可確保，如果文化特性名稱是在伺服器上的預設文化特性名稱的新<xref:System.Globalization.CultureInfo>類別建構函式所建立的物件包含文化特性的預設設定，並不會反映使用伺服器的覆寫任何設定**地區及語言選項**應用程式。 在伺服器上的任何覆寫設定的值是不存在於使用者的系統上，或會反映在使用者的輸入項目。  
  
 這個範例會剖析的日期和時間 （一個由儲存的隱藏欄位的其他使用者輸入） 的兩個字串表示，因為它會定義可能<xref:System.Globalization.CultureInfo>事先可能需要的物件。 它會建立的陣列<xref:System.Globalization.CultureInfo>物件所傳回的元素數目大於<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>屬性。 它接著會執行個體化<xref:System.Globalization.CultureInfo>物件每個語言/地區字串，並也會具現化<xref:System.Globalization.CultureInfo>物件，代表<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。  
  
 您的程式碼可以呼叫任何一個<xref:System.DateTime.Parse%2A>或<xref:System.DateTime.TryParse%2A>方法來轉換使用者的字串表示的日期和時間<xref:System.DateTime>值。 您可能需要單一的剖析作業重複的呼叫 parse 方法。 如此一來，<xref:System.DateTime.TryParse%2A>方法是更好，因為它會傳回`false`如果剖析作業會失敗。 相反地，處理重複可能擲回的例外狀況<xref:System.DateTime.Parse%2A>方法可以是非常花錢 Web 應用程式中的。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，建立[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]沒有程式碼後置的網頁。 然後將範例複製到網頁上，因此，它會取代所有現有的程式碼。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web 頁面應包含下列控制項：  
  
-   A<xref:System.Web.UI.WebControls.Label>控制項，程式碼中未參考。 設定其<xref:System.Web.UI.WebControls.TextBox.Text%2A>屬性 」 輸入的數字:"。  
  
-   名為 `DateString` 的 <xref:System.Web.UI.WebControls.TextBox> 控制項。  
  
-   名為 `OKButton` 的 <xref:System.Web.UI.WebControls.Button> 控制項。 設定其<xref:System.Web.UI.WebControls.Button.Text%2A>屬性為 [確定]。  
  
-   名為 `DateInfo` 的 <xref:System.Web.UI.WebControls.HiddenField> 控制項。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要防止使用者將指令碼插入 HTML 資料流，使用者輸入應該永遠不會直接回應伺服器在回應中。 相反地，它應該進行編碼，使用<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>方法。  
  
## <a name="see-also"></a>另請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)  
 [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)  
 [剖析日期和時間字串](../../../docs/standard/base-types/parsing-datetime.md)
