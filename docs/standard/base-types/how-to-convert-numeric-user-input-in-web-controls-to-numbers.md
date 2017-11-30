---
title: "如何：將使用者輸入 Web 控制項的數值轉換成數字"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 92e28e3b303a7523b9da69b7eb283e0261fc681c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>如何：將使用者輸入 Web 控制項的數值轉換成數字
網頁可以顯示世界中的任何位置，因為使用者可以輸入數值資料<xref:System.Web.UI.WebControls.TextBox>幾乎無限數量的格式中的控制項。 如此一來，它是使用者的非常重要，以判斷的地區設定和網頁文化特性。 當您剖析使用者輸入時，然後可以套用使用者的地區設定和文化特性所定義的格式設定慣例。  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>若要將從 Web TextBox 控制項的數字輸入轉換為數值  
  
1.  決定所傳回的字串陣列是否<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>屬性填入。 如果不是，繼續進行步驟 6。  
  
2.  如果傳回的字串陣列<xref:System.Web.HttpRequest.UserLanguages%2A>屬性填入，擷取其第一個元素。 第一個項目表示使用者的預設或慣用的語言和地區。  
  
3.  具現化<xref:System.Globalization.CultureInfo>物件，代表使用者的慣用文化特性，藉由呼叫<xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>建構函式。  
  
4.  呼叫`TryParse`或`Parse`來輸入您想要轉換的使用者數值類型的方法。 使用的多載`TryParse`或`Parse`方法`provider`參數，並將它傳遞下列任一項：  
  
    -   <xref:System.Globalization.CultureInfo>步驟 3 中建立的物件。  
  
    -   <xref:System.Globalization.NumberFormatInfo>所傳回的物件<xref:System.Globalization.CultureInfo.NumberFormat%2A>屬性<xref:System.Globalization.CultureInfo>步驟 3 中建立的物件。  
  
5.  如果轉換失敗，重複步驟 2 到 4 的字串陣列中每個剩餘的項目所傳回<xref:System.Web.HttpRequest.UserLanguages%2A>屬性。  
  
6.  如果轉換仍失敗，或傳回的字串陣列<xref:System.Web.HttpRequest.UserLanguages%2A>屬性是空的傳回使用文化特性而異，剖析字串<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>屬性。  
  
## <a name="example"></a>範例  
 下列範例是完整的程式碼後置頁面會要求使用者輸入的數字中的 Web form<xref:System.Web.UI.WebControls.TextBox>控制，並將其轉換為數字。 然後加倍，並使用相同的格式規則做為原始的輸入顯示該數字。  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>中所包含的文化特性名稱填入屬性`Accept-Language`包含在 HTTP 要求標頭。 不過，並非所有瀏覽器包括`Accept-Language`標頭中的要求，以及使用者也可以抑制標頭完全。 這使得剖析使用者輸入時，必須有後援文化特性。 一般而言，後援文化特性是所傳回的文化特性而異<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>。 使用者也可以提供 Internet Explorer 具有文化特性名稱其輸入在文字方塊中，會建立文化特性名稱可能不是有效的可能性。 這使得重要具現化時使用例外狀況處理<xref:System.Globalization.CultureInfo>物件。  
  
 從 Internet Explorer 所送出的 HTTP 要求擷取時<xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>陣列填入使用者的喜好順序。 陣列中的第一個項目包含使用者的主要文化特性/地區的名稱。 如果陣列包含任何其他項目，Internet Explorer 任意指派這些品質規範，以分號分隔的文化特性名稱。 例如，為 FR-FR 文化特性的項目可能會`fr-FR;q=0.7`。  
  
 範例會呼叫<xref:System.Globalization.CultureInfo.%23ctor%2A>建構函式與它`useUserOverride`參數設定為`false`來建立新的<xref:System.Globalization.CultureInfo>物件。 如此可確保，如果文化特性名稱是在伺服器上的預設文化特性名稱的新<xref:System.Globalization.CultureInfo>類別建構函式所建立的物件包含文化特性的預設設定，並不會反映使用伺服器的覆寫任何設定**地區及語言選項**應用程式。 在伺服器上的任何覆寫設定的值是不存在於使用者的系統上，或會反映在使用者的輸入項目。  
  
 您的程式碼可以呼叫任何一個`Parse`或`TryParse`方法的使用者輸入的數字類型會轉換成。 您可能需要單一的剖析作業重複的呼叫 parse 方法。 如此一來，`TryParse`方法是比較好，因為它會傳回`false`如果剖析作業會失敗。 相反地，處理重複可能擲回的例外狀況`Parse`方法可以是非常花錢 Web 應用程式中的。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要編譯程式碼，將複製到[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]因此它會取代所有現有的程式碼的程式碼後置頁面。 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web 頁面應包含下列控制項：  
  
-   A<xref:System.Web.UI.WebControls.Label>控制項，程式碼中未參考。 設定其<xref:System.Web.UI.WebControls.TextBox.Text%2A>屬性 」 輸入的數字:"。  
  
-   名為 `NumericString` 的 <xref:System.Web.UI.WebControls.TextBox> 控制項。  
  
-   名為 `OKButton` 的 <xref:System.Web.UI.WebControls.Button> 控制項。 設定其<xref:System.Web.UI.WebControls.Button.Text%2A>屬性為 [確定]。  
  
 從類別的名稱變更`NumericUserInput`所定義的類別名稱`Inherits`屬性[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]網頁的`Page`指示詞。 變更名稱`NumericInput`物件所定義的名稱來參考`id`屬性[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]網頁的`form`標記。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 若要防止使用者將指令碼插入 HTML 資料流，使用者輸入應該永遠不會直接回應伺服器在回應中。 相反地，它應該進行編碼，使用<xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>方法。  
  
## <a name="see-also"></a>另請參閱  
 [執行格式化作業](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [剖析數值字串](../../../docs/standard/base-types/parsing-numeric.md)
