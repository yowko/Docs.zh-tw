---
title: 如何：將使用者輸入 Web 控制項的數值轉換成數字
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 663f9d88315f396b187cca874c930179f1dea523
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2018
ms.locfileid: "47204725"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>如何：將使用者輸入 Web 控制項的數值轉換成數字
由於網頁可在世界上的任何角落顯示，所以，使用者可以幾乎不限數量的格式來將數值資料輸入至 <xref:System.Web.UI.WebControls.TextBox> 控制項。 因此，判斷網頁使用者的地區設定和文化特性就變得非常重要。 當您剖析使用者輸入時，可以接著套用使用者地區設定和文化特性所定義的格式設定慣例。  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>將來自 Web TextBox 控制項的數值輸入轉換為數字  
  
1.  判斷是否已填入由 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 屬性所傳回的字串陣列。 如果不要，請繼續進行步驟 6。  
  
2.  如果由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列已填入，請擷取它的第一個元素。 第一個元素代表使用者預設或慣用的語言和地區。  
  
3.  藉由呼叫 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> 建構函式來將代表使用者慣用文化特性的 <xref:System.Globalization.CultureInfo> 物件具現化。  
  
4.  針對您想要轉換使用者輸入的目標數值類型呼叫 `TryParse` 或 `Parse` 方法。 搭配 `provider` 參數使用 `TryParse` 或 `Parse` 方法的多載，然後將下列任一項傳遞給它：  
  
    -   在步驟 3 中建立的 <xref:System.Globalization.CultureInfo> 物件。  
  
    -   由步驟 3 中所建立 <xref:System.Globalization.CultureInfo> 物件之 <xref:System.Globalization.CultureInfo.NumberFormat%2A> 屬性所傳回的 <xref:System.Globalization.NumberFormatInfo> 物件。  
  
5.  如果轉換失敗，請針對由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回之字串陣列中的每個剩餘元素，重複執行步驟 2 到 4。  
  
6.  如果轉換仍然失敗，或由 <xref:System.Web.HttpRequest.UserLanguages%2A> 屬性所傳回的字串陣列是空的，請使用不因文化特性而異的方式來剖析字串，這是由 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 屬性所傳回。  
  
## <a name="example"></a>範例  
 下列範例是 Web 表單的完整程式碼後置頁面，此表單會要求使用者在 <xref:System.Web.UI.WebControls.TextBox> 控制項中輸入數值，並將它轉換為數字。 然後將該數字加倍，並使用與原始輸入相同的格式規則來顯示。  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> 屬性會從 HTTP 要求所含之 `Accept-Language` 標頭內含的文化特性名稱來填入。 不過，並非所有瀏覽器都會在其要求中包含 `Accept-Language` 標頭，而使用者也可以完全抑制標頭。 這在剖析使用者輸入時，會使得具備後援文化特性變得很重要。 一般而言，後援文化特性是 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 所傳回的文化特性，但 它不因文化特性而異。 使用者也可以在文字方塊中輸入文化特性名稱以提供給 Internet Explorer，但這可能會導致文化特性名稱無效。 如此一來，將 <xref:System.Globalization.CultureInfo> 物件具現化時，使用例外狀況處理就變得很重要。  
  
 從 Internet Explorer 提交的 HTTP 要求中進行擷取時，會依照使用者喜好設定順序填入 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>。 陣列中的第一個元素會包含使用者主要文化特性/地區的名稱。 如果陣列包含任何其他項目，Internet Explorer 就會為它們任意指派一個品質指定名稱，以分號分隔文化特性名稱。 例如，適用於 fr-FR 文化特性的項目可能採取 `fr-FR;q=0.7` 的形式。  
  
 範例會搭配已設定為 `false` 的 `useUserOverride` 參數呼叫 <xref:System.Globalization.CultureInfo.%23ctor%2A> 建構函式，以建立新的 <xref:System.Globalization.CultureInfo> 物件。 這可確保在文化特性名稱為伺服器預設文化特性名稱的情況下，由類別建構函式所建立的新 <xref:System.Globalization.CultureInfo> 物件就會包含文化特性的預設設定，而且不會反映使用伺服器的**地區及語言選項**應用程式所覆寫的任何設定。 來自伺服器上任何已覆寫設定的值可能不存在於使用者的系統上或反映於使用者的輸入中。  
  
 您的程式碼可以針對將轉換使用者輸入的目標數值類型呼叫 `Parse` 或 `TryParse` 方法。 您可能需要針對單一剖析作業重複呼叫剖析方法。 因此，`TryParse` 方法比較好，因為它會在剖析作業失敗時傳回 `false`。 相反地，在 Web 應用程式中處理 `Parse` 方法可能擲回的重複例外狀況，是個非常耗費成本的作法。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，請將它複製到 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 程式碼後置頁面，以便它取代所有現有的程式碼。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 網頁應包含下列控制項：  
  
-   <xref:System.Web.UI.WebControls.Label> 控制項，程式碼中並未參考此控制項。 將它的 <xref:System.Web.UI.WebControls.TextBox.Text%2A> 屬性設定為 "Enter a Number:"。  
  
-   名為 `NumericString` 的 <xref:System.Web.UI.WebControls.TextBox> 控制項。  
  
-   名為 `OKButton` 的 <xref:System.Web.UI.WebControls.Button> 控制項。 將它的 <xref:System.Web.UI.WebControls.Button.Text%2A> 屬性設為 "OK"。  
  
 將來自 `NumericUserInput` 的類別名稱變更為由 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 頁面之 `Page` 指示詞的 `Inherits` 屬性所定義的類別名稱。 將 `NumericInput` 物件參考的名稱變更為 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 頁面之 `form` 標籤的 `id` 屬性所定義的名稱。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 為了防止使用者將指令碼插入至 HTML 資料流，絕對不應在伺服器回應中直接回應使用者輸入。 而應改用 <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType> 方法進行編碼。  
  
## <a name="see-also"></a>另請參閱

- [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)  
- [剖析數值字串](../../../docs/standard/base-types/parsing-numeric.md)
