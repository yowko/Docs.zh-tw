---
title: UI 自動化 TextPattern 概觀
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 522caed7e8006157f99e65e99bf52743871444ad
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646346"
---
# <a name="ui-automation-textpattern-overview"></a>UI 自動化 TextPattern 概觀
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本概觀說明如何使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 來公開 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]支援平台中，文字控制項的文字內容，包括格式和樣式屬性。 這些控制項包括但不限於 Microsoft.NET Framework<xref:System.Windows.Controls.TextBox>並<xref:System.Windows.Controls.RichTextBox>，以及其[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]對等項目。  
  
 若要公開控制項的文字內容，您可以使用 <xref:System.Windows.Automation.TextPattern> 控制項模式，它會將文字容器的內容表示成文字資料流。 接著， <xref:System.Windows.Automation.TextPattern> 會需要 <xref:System.Windows.Automation.Text.TextPatternRange> 類別的支援來公開格式和樣式屬性。 <xref:System.Windows.Automation.Text.TextPatternRange> 可支援 <xref:System.Windows.Automation.TextPattern> ，其方法是使用 <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> 和 <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> 端點的集合，來表示文字容器中的連續或多個非連續文字範圍。 <xref:System.Windows.Automation.Text.TextPatternRange> 可支援選取、比較、擷取和周遊之類的功能。  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> 類別沒有提供插入或修改文字的方法。 不過，依據控制項，可能可以藉由 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> 或透過直接鍵盤輸入來完成此作業。 請參閱[TextPattern Insert Text Sample](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)的範例。  
  
 對輔助技術廠商及其使用者而言，本概觀中所描述的功能非常重要。 輔助技術可以使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 來收集使用者的完整文字格式化資訊，並依 <xref:System.Windows.Automation.Text.TextUnit> (字元、單字、字行或段落) 提供以程式設計方式巡覽和選取文字的功能。  
  
<a name="UI_Automation_TextPattern_vs__Cicero"></a>   
## <a name="ui-automation-textpattern-vs-text-services-framework"></a>UI 自動化 TextPattern 與Text Services Framework (TSF)  
 [!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)] 是簡單且可調整的系統架構，可在桌面上和應用程式中啟用自然語言服務及進階文字輸入。 除了提供介面讓應用程式公開其文字存放區之外，它也支援該文字存放區的中繼資料。  
  
 不過， [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] 是針對需要將輸入插入內容感知案例中的應用程式所設計，而 <xref:System.Windows.Automation.TextPattern> 是唯讀方案 (具有上述有限的因應措施)，目的是要為螢幕助讀程式和 Braille 裝置提供最佳化的文字存放區存取方式。  
  
 簡言之，需要對文字存放區進行唯讀存取的可存取技術，可以使用 <xref:System.Windows.Automation.TextPattern>，但需要較複雜的 [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] 功能，才能進行內容感知輸入。  
  
<a name="Control_Types"></a>   
## <a name="control-types"></a>控制項類型  
  
#### <a name="text"></a>Text  
 文字控制項是用來表示螢幕上一段文字的基本項目。  
  
 獨立的文字控制項可以用來當做標籤或表單上的靜態文字。 文字控制項也可以包含在 <xref:System.Windows.Automation.ControlType.ListItem>、 <xref:System.Windows.Automation.ControlType.TreeItem> 或 <xref:System.Windows.Automation.ControlType.DataItem>的結構內。  
  
> [!NOTE]
>  文字控制項可能不會出現在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的內容檢視中 (請參閱 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md))。 這是因為文字控制項通常是透過另一個控制項的名稱屬性來顯示。 比方說，用來標示編輯控制項的文字，會透過編輯控制項的名稱屬性來顯示。 因為編輯控制項是在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀目錄的內容檢視中，所以文字項目本身不需要在 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 樹狀結構的那個檢視中。 內容檢視中唯一出現的文字是非多餘資訊的文字。 這可以讓任何輔助技術只在其使用者需要的資訊項目上快速篩選。  
  
#### <a name="edit"></a>Edit  
 編輯控制項可讓使用者檢視和編輯單行文字。  
  
> [!NOTE]
>  在某些配置案例中，單行文字可能會換行。  
  
#### <a name="document"></a>文件  
 文件控制項可讓使用者巡覽及取得多頁文字中的資訊。  
  
<a name="TextPattern_Client_API_s"></a>   
## <a name="textpattern-client-apis"></a>TextPattern 用戶端 API  
  
|||  
|-|-|  
|`System.Windows.Automation.TextPattern Class`|[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 文字模型的進入點。<br /><br /> 這個類別也包含下列兩個 <xref:System.Windows.Automation.TextPattern> 事件接聽程式： <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> 和 <xref:System.Windows.Automation.TextPattern.TextChangedEvent>。|  
|`System.Windows.Automation.Text.TextPatternRange Class`|支援 <xref:System.Windows.Automation.TextPattern>之文字容器內的一段文字表示法。<br /><br /> 使用者介面自動化用戶端應謹慎處理使用 <xref:System.Windows.Automation.Text.TextPatternRange>建立之文字範圍的目前有效性。 如果文字控制項中的原始文字完全被新的文字所取代，目前的文字範圍就會變成無效。 不過，如果只有部分原始文字變更，且基礎文字控制項是使用錨點 (或端點) 來管理其文字「指標」，而不是使用絕對字元定位，則文字範圍可能仍有一些可行性。<br /><br /> 用戶端可以接聽 <xref:System.Windows.Automation.TextPattern.TextChangedEvent> ，以取得其使用之文字內容的任何變更通知。|  
|`System.Windows.Automation.AutomationTextAttribute Class`|用來識別文字範圍的格式化屬性。|  
  
<a name="TextPattern_Provider_API_s"></a>   
## <a name="textpattern-provider-apis"></a>TextPattern 提供者 API  
 藉由實作 <xref:System.Windows.Automation.TextPattern> 和 <xref:System.Windows.Automation.Provider.ITextProvider> 介面 (原生或透過 <xref:System.Windows.Automation.Provider.ITextRangeProvider> Proxy) 來支援 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 的 UI 項目或控制項，除了提供強大的巡覽功能，還能夠公開其包含之任何文字的詳細屬性資訊。  
  
 如果控制項不支援任何特定屬性，則 <xref:System.Windows.Automation.TextPattern> 提供者不需要支援所有文字屬性。  
  
 如果控制項支援文字區域內之文字游標 (或系統游標) 的文字選取範圍或位置，則 <xref:System.Windows.Automation.TextPattern> 提供者必須支援 <xref:System.Windows.Automation.TextPattern.GetSelection%2A> 和 <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> 函式。 如果控制項不支援這項功能，就不需要支援其中任一種方法。 不過，控制項必須實作 <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> 屬性，以公開其支援的文字選取範圍類型。  
  
 <xref:System.Windows.Automation.TextPattern> 提供者必須一律支援 <xref:System.Windows.Automation.Text.TextUnit> 常數 <xref:System.Windows.Automation.Text.TextUnit.Character> 和 <xref:System.Windows.Automation.Text.TextUnit.Document> ，以及它能夠支援的任何其他 <xref:System.Windows.Automation.Text.TextUnit> 常數。  
  
> [!NOTE]
>  如果提供者要略過針對特定 <xref:System.Windows.Automation.Text.TextUnit> 的支援，可以延遲到所支援的下一個最大 <xref:System.Windows.Automation.Text.TextUnit> ，順序如下： <xref:System.Windows.Automation.Text.TextUnit.Character>、 <xref:System.Windows.Automation.Text.TextUnit.Format>、 <xref:System.Windows.Automation.Text.TextUnit.Word>、 <xref:System.Windows.Automation.Text.TextUnit.Line>、 <xref:System.Windows.Automation.Text.TextUnit.Paragraph>、 <xref:System.Windows.Automation.Text.TextUnit.Page>和 <xref:System.Windows.Automation.Text.TextUnit.Document>。  
  
|||  
|-|-|  
|`ITextProvider Interface`|公開用戶端應用程式中支援 <xref:System.Windows.Automation.TextPattern> 的方法、屬性 (property) 和屬性 (attribute)，請參閱 <xref:System.Windows.Automation.Provider.ITextProvider>。|  
|`ITextRangeProvider Interface`|表示文字提供者中的一段文字，請參閱 <xref:System.Windows.Automation.Provider.ITextRangeProvider>。|  
|`System.Windows.Automation.TextPatternIdentifiers Class`|包含用來做為文字提供者識別項的值，請參閱 <xref:System.Windows.Automation.TextPatternIdentifiers>。|  
  
<a name="Security"></a>   
## <a name="security"></a>安全性  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]架構的設計將安全性納入考量 (請參閱 < [UI 自動化安全性概觀](../../../docs/framework/ui-automation/ui-automation-security-overview.md))。 不過，本概觀中所描述的 TextPattern 類別，需要一些特定的安全性考量。  
  
-   [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 文字提供者提供唯讀介面，而且不提供變更控制項中現有文字的能力。  
  
-   使用者介面自動化用戶端在完全「受信任」的情況下，只能使用 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 。 此案例的範例之一，就是受保護的登入桌面，只有已知且受信任的應用程式可以在上面執行。  
  
-   使用者介面自動化提供者的開發人員應該要知道，他們選擇透過 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 公開在其控制項中的所有資訊，基本上是公用的，而且完全可供其他程式碼存取。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 完全不會判斷任何使用者介面自動化用戶端的可信度，因此，使用者介面自動化提供者不應公開受保護的內容或敏感的文字資訊 (例如密碼欄位)。  
  
-   [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] 安全性最重要的變更之一，統稱為「安全輸入」，其中包含最低權限 (或有限) 使用者帳戶 (LUA) 和 UI 權限層級隔離 (UIPI) 等技術。  
  
    -   UIPI 會防止一個程式控制及/或監視另一個「權限」更高的程式，以防止詐騙使用者輸入的跨處理序視窗訊息攻擊。  
  
    -   LUA 會針對系統管理員群組中之使用者所執行的應用程式，設定權限的限制。 應用程式不一定要有系統管理員權限，但是會以所需的最低權限來執行。 因此，可能會在 LUA 案例中強制執行一些限制。 最值得注意的字串截斷 (包括 TextPattern 字串)，其中可能需要限制從系統管理員層級應用程式擷取的字串大小，因此不會強制其將記憶體配置到停用應用程式的點。  
  
<a name="Performance"></a>   
## <a name="performance"></a>效能  
 由於 TextPattern 依賴跨處理序呼叫來執行其大部分的功能，因此它沒有提供快取機制來改善處理內容時的效能。 這一點不同於 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] 中，可以使用 <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> 或 <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> 方法來存取的其他控制項模式。  
  
 改善效能的一個策略，就是確定使用者介面自動化用戶端會使用 <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>，嘗試擷取適當調整大小的文字區塊。 例如，GetText(1) 呼叫會針對每個字元產生跨處理序叫用，而一個 GetText(-1) 呼叫將會產生一個跨處理序叫用，但是依據文字提供者的大小，可以有高延遲。  
  
<a name="Glossary"></a>   
## <a name="textpattern-terminology"></a>TextPattern 術語  
 **屬性**  
 文字範圍的格式化特性 (例如， <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> 或 <xref:System.Windows.Automation.TextPattern.FontNameAttribute>)。  
  
 **變質範圍**  
 變質範圍是空白或零個字元的文字範圍。 就 TextPattern 控制項模式的目的而言，文字插入點 (或系統游標) 會被視為變質範圍。 如果沒有選取文字， <xref:System.Windows.Automation.TextPattern.GetSelection%2A> 會在文字插入點傳回變質範圍，而 <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> 會傳回變質範圍，做為其起始端點。 當文字提供者找不到符合指定條件的任何文字範圍時，<xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> 和 <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> 可能會傳回變質範圍。 這個變質範圍可以用來當做文字提供者內的開始端點。 <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> 並<xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A>會傳回 null 參考 (`Nothing`在 Microsoft Visual Basic.NET) 以避免與探索到的範圍與變質範圍混淆。  
  
 **內嵌物件**  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 文字模型中有兩種類型的內嵌物件 。 其中包含以文字為基礎的內容項目 (例如超連結或資料表)，以及控制項目 (例如影像和按鈕)。 如需詳細資訊，請參閱 [Access Embedded Objects Using UI Automation](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md)。  
  
 **端點**  
 文字容器內之文字範圍的絕對 <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> 或 <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> 點。  
  
 ![TextPatternRangeEndpoints&#40;的開頭與結尾&#41;。](../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")  
下列範例說明一組開始和結束點。  
  
 **TextRange**  
 表示包含所有相關聯屬性和功能的文字容器中的一段文字，有開始和結束點。  
  
 <xref:System.Windows.Automation.Text.TextUnit>  
 預先定義的文字單位 (字元、單字、字行或段落)，用於巡覽文字範圍的邏輯區段。  
  
## <a name="see-also"></a>另請參閱  
 [用戶端的 UI 自動化控制項模式](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI 自動化控制項模式概觀](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [在 UI 自動化中使用快取](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [支援 UI 自動化提供者的控制項模式](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [UI 自動化用戶端的控制項模式對應](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
 [Text Services Framework](https://msdn.microsoft.com/library/default.asp?url=/library/tsf/tsf/text_services_framework.asp)
