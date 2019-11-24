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
ms.openlocfilehash: ceab7db1f9eeb47ec020e220ec702af8181855e2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442487"
---
# <a name="ui-automation-and-screen-scaling"></a>UI 自動化和畫面縮放比例
> [!NOTE]
> 這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。  
  
Starting with Windows Vista, Windows enables users to change the dots per inch (dpi) setting so that most user interface (UI) elements on the screen appear larger. Although this feature has long been available in Windows, in previous versions the scaling had to be implemented by applications. Starting with Windows Vista, the Desktop Window Manager performs default scaling for all applications that do not handle their own scaling. 使用者介面自動化用戶端應用程式必須將這項功能納入考量。  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista 中的縮放比例  
 The default dpi setting is 96, which means that 96 pixels occupy a width or height of one notional inch. 「英吋」的確切測量值取決於監視器的大小和實體解析度。 例如，在 12 英吋寬、1280 像素水平解析度的監視器上，96 像素的水平線長度約一英吋的 9/10。  
  
 Changing the dpi setting is not the same as changing the screen resolution. With dpi scaling, the number of physical pixels on the screen remains the same. 不過，縮放比例會套用至 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的大小和位置。 針對未明確要求不縮放的桌面和應用程式，桌面視窗管理員 (DWM) 會自動執行縮放。  
  
 In effect, when the user sets the scale factor to 120 dpi, a vertical or horizontal inch on the screen becomes bigger by 25 percent. 所有維度都會因此調整。 來自畫面上方和左邊緣的應用程式視窗位移會增加 25%。 If application scaling is enabled and the application is not dpi-aware, the size of the window increases in the same proportion, along with the offsets and sizes of all [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elements it contains.  
  
> [!NOTE]
> By default, the DWM does not perform scaling for non-dpi-aware applications when the user sets the dpi to 120, but does perform it when the dpi is set to a custom value of 144 or higher. 不過，使用者可以覆寫此預設行為。  
  
 針對重視畫面座標的應用程式，畫面縮放比例會產生新挑戰。 畫面現在包含兩個座標系統：實體和邏輯。 點的實體座標是來自原點左上方的實際位移 (以像素為單位)。 邏輯座標則是像素本身縮放時，跟著縮放的位移。  
  
 假設您設計的對話方塊在座標 (100, 48) 上有一個按鈕。 When this dialog box is displayed at the default 96 dpi, the button is located at physical coordinates of (100, 48). At 120 dpi, it is located at physical coordinates of (125, 60). But the logical coordinates are the same at any dpi setting: (100, 48).  
  
 Logical coordinates are important, because they make the behavior of the operating system and applications consistent regardless of the dpi setting. 例如， <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType> 一般會傳回邏輯座標。 If you move the cursor over an element in a dialog box, the same coordinates are returned regardless of the dpi setting. If you draw a control at (100, 100), it is drawn to those logical coordinates, and will occupy the same relative position at any dpi setting.  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>使用者介面自動化用戶端中的縮放比例  
 The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] API does not use logical coordinates. 下列方法和屬性會傳回實體座標或採用它們做為參數。  
  
- <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 By default, a UI Automation client application running in a non-96- dpi environment will not be able to obtain correct results from these methods and properties. 例如，因為游標位置是在邏輯座標中，用戶端無法單純地將這些座標傳遞至 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> ，以取得游標下的項目。 此外，應用程式也將無法在其用戶端區域之外正確放置視窗。  
  
 解決方法分為兩個部分。  
  
1. First, make the client application dpi-aware. 若要執行這項動作，請在啟動時呼叫 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 函式 `SetProcessDPIAware` 。 以 Managed 程式碼的下列宣告，讓這個函式成為可用的。  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     This function makes the entire process dpi-aware, meaning that all windows that belong to the process are unscaled. In the [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter), for instance, the four windows that make up the highlight rectangle are located at the physical coordinates obtained from UI Automation, not the logical coordinates. If the sample were not dpi-aware, the highlight would be drawn at the logical coordinates on the desktop, which would result in incorrect placement in a non-96- dpi environment.  
  
2. 若要取得游標座標，請呼叫 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 函式 `GetPhysicalCursorPos`。 下列範例顯示如何宣告及使用這個函式。  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
> 請勿使用 <xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>。 這個屬性在縮放環境中用戶端視窗之外的行為是未定義的。  
  
 If your application performs direct cross-process communication with non- dpi-aware applications, you may have convert between logical and physical coordinates by using the [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] functions `PhysicalToLogicalPoint` and `LogicalToPhysicalPoint`.  
  
## <a name="see-also"></a>請參閱

- [Highlighter Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/Highlighter)
