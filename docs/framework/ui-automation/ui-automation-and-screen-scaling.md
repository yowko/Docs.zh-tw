---
title: UI 自動化和畫面縮放比例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
ms.openlocfilehash: 35b46d2030ee887eb98618fbed127097cec1f0c5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044189"
---
# <a name="ui-automation-and-screen-scaling"></a>UI 自動化和畫面縮放比例
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]可讓使用者變更 [每英寸的時數 (DPI)] 設定[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] , 讓螢幕上的大部分元素看起來更大。 雖然在 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]中早已經提供這項功能，但在舊版中，縮放比例必須由應用程式實作。 在 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]中，桌面視窗管理員會針對所有不處理其本身縮放比例的應用程式執行預設的縮放功能。 使用者介面自動化用戶端應用程式必須將這項功能納入考量。  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista 中的縮放比例  
 預設 DPI 設定為 96, 這表示96圖元的寬度或高度會占一個名義英寸。 「英吋」的確切測量值取決於監視器的大小和實體解析度。 例如，在 12 英吋寬、1280 像素水平解析度的監視器上，96 像素的水平線長度約一英吋的 9/10。  
  
 變更 DPI 設定與變更螢幕解析度不同。 使用 DPI 縮放比例時, 螢幕上的實體圖元數目會維持不變。 不過，縮放比例會套用至 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的大小和位置。 針對未明確要求不縮放的桌面和應用程式，桌面視窗管理員 (DWM) 會自動執行縮放。  
  
 實際上, 當使用者將縮放比例設定為 120 DPI 時, 螢幕上的垂直或水準英寸會變大達 25%。 所有維度都會因此調整。 來自畫面上方和左邊緣的應用程式視窗位移會增加 25%。 如果應用程式調整已啟用, 且應用程式不能感知 DPI, 則視窗的大小會以相同比例增加, 連同其包含的所有[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]元素的位移和大小。  
  
> [!NOTE]
> 根據預設, 當使用者將 DPI 設定為120時, DWM 不會針對非 DPI 感知的應用程式執行調整, 但會在 DPI 設定為144或更高的自訂值時執行。 不過，使用者可以覆寫此預設行為。  
  
 針對重視畫面座標的應用程式，畫面縮放比例會產生新挑戰。 畫面現在包含兩個座標系統：實體和邏輯。 點的實體座標是來自原點左上方的實際位移 (以像素為單位)。 邏輯座標則是像素本身縮放時，跟著縮放的位移。  
  
 假設您設計的對話方塊在座標 (100, 48) 上有一個按鈕。 以預設 96 DPI 顯示此對話方塊時, 按鈕會位於 (100, 48) 的實體座標中。 在 120 DPI 中, 它位於 (125, 60) 的實體座標。 但是邏輯座標在任何 DPI 設定中都相同:(100、48)。  
  
 邏輯座標很重要, 因為不論 DPI 設定為何, 它們都會讓作業系統和應用程式的行為保持一致。 例如， <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> 一般會傳回邏輯座標。 如果您將游標移到對話方塊中的專案上方, 則會傳回相同的座標, 不論 DPI 設定為何。 如果您在 (100, 100) 繪製控制項, 則會將它繪製到那些邏輯座標, 而且會佔用與任何 DPI 設定相同的相對位置。  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>使用者介面自動化用戶端中的縮放比例  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API 不會使用邏輯座標。 下列方法和屬性會傳回實體座標或採用它們做為參數。  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 根據預設, 在非 96 DPI 環境中執行的使用者介面自動化用戶端應用程式將無法從這些方法和屬性取得正確的結果。 例如，因為游標位置是在邏輯座標中，用戶端無法單純地將這些座標傳遞至 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> ，以取得游標下的項目。 此外，應用程式也將無法在其用戶端區域之外正確放置視窗。  
  
 解決方法分為兩個部分。  
  
1. 首先, 將用戶端應用程式設為 DPI 感知。 若要執行這項動作，請在啟動時呼叫 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 函式 `SetProcessDPIAware` 。 以 Managed 程式碼的下列宣告，讓這個函式成為可用的。  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     此函式會使整個進程 DPI 感知, 這表示屬於該進程的所有視窗都是無比例的。 例如, 在[螢光筆的範例](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)中, 構成反白顯示矩形的四個視窗位於從 UI 自動化取得的實體座標, 而非邏輯座標。 如果範例不是 DPI 感知, 就會在桌面的邏輯座標上繪製反白顯示, 這會導致非 96 DPI 環境中的位置不正確。  
  
2. 若要取得游標座標，請呼叫 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 函式 `GetPhysicalCursorPos`。 下列範例顯示如何宣告及使用這個函式。  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> 請勿使用 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>。 這個屬性在縮放環境中用戶端視窗之外的行為是未定義的。  
  
 如果您的應用程式執行與非 DPI 感知應用程式的直接跨進程通訊, 您可能會使用[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] `PhysicalToLogicalPoint`函式和`LogicalToPhysicalPoint`, 在邏輯和實體座標之間轉換。  
  
## <a name="see-also"></a>另請參閱

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
