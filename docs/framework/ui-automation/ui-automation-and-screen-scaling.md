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
ms.openlocfilehash: 2a68a74fa6aadcaba21f142d394a1f8a3d8af371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179971"
---
# <a name="ui-automation-and-screen-scaling"></a>UI 自動化和畫面縮放比例
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
從 Windows Vista 開始，Windows 使使用者能夠更改每英寸點 （DPI） 設置，以便螢幕上的大多數使用者介面 （UI） 元素看起來更大。 儘管此功能在 Windows 中早已可用，但在以前的版本中，縮放必須由應用程式實現。 桌面視窗管理員從 Windows Vista 開始，對所有不處理其自身縮放的應用程式執行預設縮放。 使用者介面自動化用戶端應用程式必須將這項功能納入考量。  
  
<a name="Scaling_in_Windows_Vista"></a>
## <a name="scaling-in-windows-vista"></a>Windows Vista 中的縮放比例  
 預設 DPI 設置為 96，這意味著 96 圖元佔用一個名義英寸的寬度或高度。 「英吋」的確切測量值取決於監視器的大小和實體解析度。 例如，在 12 英吋寬、1280 像素水平解析度的監視器上，96 像素的水平線長度約一英吋的 9/10。  
  
 更改 DPI 設置與更改螢幕解析度不同。 使用 DPI 縮放時，螢幕上的物理圖元數保持不變。 不過，縮放比例會套用至 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的大小和位置。 針對未明確要求不縮放的桌面和應用程式，桌面視窗管理員 (DWM) 會自動執行縮放。  
  
 實際上，當使用者將比例因數設置為 120 DPI 時，螢幕上的垂直或水準英寸會變大 25%。 所有維度都會因此調整。 來自畫面上方和左邊緣的應用程式視窗位移會增加 25%。 如果啟用了應用程式縮放，並且應用程式不具有 DPI 感知功能，則視窗的大小將隨其比例的增加，以及它包含的所有[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]元素的偏移量和大小。  
  
> [!NOTE]
> 預設情況下，當使用者將 DPI 設置為 120 時，DWM 不會對非 DPI 感知應用程式執行縮放，但在 DPI 設置為 144 或更高的自訂值時確實執行縮放。 不過，使用者可以覆寫此預設行為。  
  
 針對重視畫面座標的應用程式，畫面縮放比例會產生新挑戰。 畫面現在包含兩個座標系統：實體和邏輯。 點的實體座標是來自原點左上方的實際位移 (以像素為單位)。 邏輯座標則是像素本身縮放時，跟著縮放的位移。  
  
 假設您設計的對話方塊在座標 (100, 48) 上有一個按鈕。 當此對話方塊顯示在預設的 96 DPI 時，該按鈕位於物理座標 （100， 48）。 在 120 DPI 處，它位於物理座標 （125， 60）。 但是邏輯座標在任何 DPI 設置中都是相同的：（100，48）。  
  
 邏輯座標很重要，因為它們使作業系統和應用程式的行為一致，而不管 DPI 設置如何。 例如， <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> 一般會傳回邏輯座標。 如果將游標移到對話方塊中的元素上，則無論 DPI 設置如何，都會返回相同的座標。 如果繪製控制項（100，100），則該控制項將繪製到這些邏輯座標，並將在任何 DPI 設置中佔據相同的相對位置。  
  
<a name="Scaling_in_UI_Automation_Clients"></a>
## <a name="scaling-in-ui-automation-clients"></a>使用者介面自動化用戶端中的縮放比例  
 API[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]不使用邏輯座標。 下列方法和屬性會傳回實體座標或採用它們做為參數。  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 預設情況下，在非 96-DPI 環境中運行的 UI 自動化用戶端應用程式將無法從這些方法和屬性中獲得正確的結果。 例如，因為游標位置是在邏輯座標中，用戶端無法單純地將這些座標傳遞至 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> ，以取得游標下的項目。 此外，應用程式也將無法在其用戶端區域之外正確放置視窗。  
  
 解決方法分為兩個部分。  
  
1. 首先，使用戶端應用程式 DPI 感知。 為此，在啟動時調用 Win32`SetProcessDPIAware`函數。 以 Managed 程式碼的下列宣告，讓這個函式成為可用的。  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     此函數使整個進程具有 DPI 感知功能，這意味著屬於該進程的所有視窗都未縮放。 例如，在[螢光筆示例中](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)，構成高光矩形的四個視窗位於從 UI 自動化獲得的物理座標，而不是邏輯座標。 如果示例不具有 DPI 感知，則高光將在桌面上的邏輯座標處繪製，這將導致在非 96-DPI 環境中放置不正確。  
  
2. 要獲取游標座標，請調用 Win32`GetPhysicalCursorPos`函數 。 下列範例顯示如何宣告及使用這個函式。  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> 請勿使用 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>。 這個屬性在縮放環境中用戶端視窗之外的行為是未定義的。  
  
 如果應用程式與非 DPI 感知應用程式執行直接跨進程通信，則可能使用 Win32 函數`PhysicalToLogicalPoint`和`LogicalToPhysicalPoint`在邏輯座標和物理座標之間進行轉換。  
  
## <a name="see-also"></a>另請參閱

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
