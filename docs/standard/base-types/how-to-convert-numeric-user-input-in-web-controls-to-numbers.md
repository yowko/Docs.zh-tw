---
title: "如何：將使用者輸入 Web 控制項的數值轉換成數字 | Microsoft Docs"
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
  - "將使用者輸入的數值轉換成數字"
  - "格式化 [.NET Framework], 數字"
  - "數字格式化 [.NET Framework]"
  - "數字 [.NET Framework], 將使用者輸入的數值轉換成數字"
  - "數值格式字串 [.NET Framework]"
  - "剖析字串 [.NET Framework], 數值字串"
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：將使用者輸入 Web 控制項的數值轉換成數字
由於網頁可在任何地方顯示，因此使用者可在 <xref:System.Web.UI.WebControls.TextBox> 控制項中輸入幾乎無限多種格式的數值。  所以，務必決定網頁使用者的地區設定和文化特性。  當您剖析使用者輸入時，就可以接著套用使用者地區設定和文化特性定義的格式化慣例。  
  
### 將 Web TextBox 控制項的數值輸入轉換成數字  
  
1.  判斷 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 屬性傳回的字串陣列是否已填入。  如果尚未填入，則繼續進行步驟 6。  
  
2.  如果 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列已填入，就會擷取它的第一個項目。  第一個項目指出使用者的預設或慣用的語言和區域。  
  
3.  呼叫 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=fullName> 建構函式以具現化 <xref:System.Globalization.CultureInfo> 物件，此物件代表使用者慣用的文化特性。  
  
4.  呼叫要將使用者輸入轉換成之數值型別的 `TryParse` 或 `Parse` 方法。  使用 `TryParse` 或 `Parse` 方法的多載與 `provider` 參數，並將下列任一項傳遞給該多載：  
  
    -   在步驟 3 中建立的 <xref:System.Globalization.CultureInfo> 物件。  
  
    -   在步驟 3 中所建立 <xref:System.Globalization.CultureInfo> 物件的 <xref:System.Globalization.CultureInfo.NumberFormat%2A> 屬性傳回的 <xref:System.Globalization.NumberFormatInfo> 物件。  
  
5.  如果轉換失敗，則針對 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性傳回的字串陣列中其餘每一個項目重複步驟 2 到 4。  
  
6.  如果轉換還是失敗，或者，如果 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列為空白，請使用由 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 屬性所傳回的 Invariant 文化特性 \(不因文化特定而異\) 來剖析字串。  
  
## 範例  
 以下範例是 Web Form 的完整程式碼後置頁，會要求使用者在 <xref:System.Web.UI.WebControls.TextBox> 控制項中輸入數值，並將它轉換成數字。  接著該數字會加倍，並且使用與原始輸入相同的格式化規則顯示。  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 屬性會從 HTTP 要求所包含 `Accept-Language` 標頭中的文化特性名稱填入。  不過，並非所有瀏覽器的要求都包含 `Accept-Language` 標頭，而且使用者可以完全隱藏標頭。  因此，剖析使用者輸入時務必有後援文化特性。  通常後援文化特性是 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> 傳回的不因國別而異的文化特性。  使用者也可以將文字方塊中輸入的文化特性名稱提供給 Internet Explorer，如此可能讓文化特性名稱無效。  因此具現化 <xref:System.Globalization.CultureInfo> 物件時，務必使用例外狀況處理。  
  
 從 Internet Explorer 提交的 HTTP 要求擷取時，<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=fullName> 陣列會依使用者偏好設定填入。  陣列中的第一個項目包含使用者主要文化特性\/區域的名稱。  如果陣列包含任何額外的項目，Internet Explorer 會為這些項目指派任意限定規範，並且使用分號與文化特性名稱分隔。  例如，fr\-FR 文化特性的項目可能採用這個格式 `fr-FR;q=0.7`。  
  
 範例會呼叫 <xref:System.Globalization.CultureInfo.%23ctor%2A> 建構函式，且其 `useUserOverride` 參數會設為 `false`，以建立新的 <xref:System.Globalization.CultureInfo> 物件。  如此可確定，如果文化特性名稱是伺服器上預設的文化特性名稱，則類別建構函式建立的 <xref:System.Globalization.CultureInfo> 物件會包含文化特性的預設設定，並且不會反映使用伺服器的 \[**地區及語言選項**\] 應用程式覆寫的任何設定。  伺服器上任何覆寫設定的值都不會出現在使用者的系統上，或是反映在使用者輸入中。  
  
 您的程式碼可以呼叫使用者輸入將轉換成的數值型別之 `Parse` 或 `TryParse` 方法。  您可能需要針對單一剖析作業重複呼叫剖析方法。  因此 `TryParse` 方法可能較佳，因為它會在剖析作業失敗時傳回 `false`。  相反地，對於 Web 應用程式而言，處理 `Parse` 方法可能擲回的重複例外狀況可能是相當耗費資源的方法。  
  
## 編譯程式碼  
 若要編譯程式碼，請將它複製到 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 程式碼後置頁，以取代所有現有的程式碼。  [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網頁應包含下列控制項：  
  
-   <xref:System.Web.UI.WebControls.Label> 控制項，程式碼中並未參考這個控制項。  將 <xref:System.Web.UI.WebControls.TextBox.Text%2A> 屬性設為 \[輸入數字：\]。  
  
-   名為 `NumericString` 的 <xref:System.Web.UI.WebControls.TextBox> 控制項。  
  
-   名為 `OKButton` 的 <xref:System.Web.UI.WebControls.Button> 控制項。  將 <xref:System.Web.UI.WebControls.Button.Text%2A> 屬性設為 \[確定\]。  
  
 將類別的名稱從 `NumericUserInput` 變更為 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 頁面之 `Page` 指示詞的 `Inherits` 屬性所定義的類別名稱。  接著，將 `NumericInput` 物件參考的名稱變更為 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 頁面之 `form` 標記的 `id` 屬性所定義的名稱。  
  
## .NET Framework 安全性  
 為避免使用者將指令碼插入 HTML 資料流中，絕不可將使用者輸入直接回應 \(Echo\) 至伺服器回應中。  而是使用 <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=fullName> 方法將使用者輸入編碼。  
  
## 請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)   
 [剖析數值字串](../../../docs/standard/base-types/parsing-numeric.md)