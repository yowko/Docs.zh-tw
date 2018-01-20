---
title: "UI 自動化和畫面縮放比例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scaling, screens
- screens, scaling
- UI (user interface), automation
- UI Automation
ms.assetid: 4380cad7-e509-448f-b9a5-6de042605fd4
caps.latest.revision: "16"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bb33d3175cf9e43797125b47c811042771e45782
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ui-automation-and-screen-scaling"></a>UI 自動化和畫面縮放比例
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] 可讓使用者變更 [!INCLUDE[TLA#tla_dpi](../../../includes/tlasharptla-dpi-md.md)] 設定，以便讓畫面上大部分的 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 項目看起來較大。 雖然在 [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)]中早已經提供這項功能，但在舊版中，縮放比例必須由應用程式實作。 在 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)]中，桌面視窗管理員會針對所有不處理其本身縮放比例的應用程式執行預設的縮放功能。 使用者介面自動化用戶端應用程式必須將這項功能納入考量。  
  
<a name="Scaling_in_Windows_Vista"></a>   
## <a name="scaling-in-windows-vista"></a>Windows Vista 中的縮放比例  
 預設的 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定是 96，表示 96 像素佔會用一英吋的寬度或高度。 「英吋」的確切測量值取決於監視器的大小和實體解析度。 例如，在 12 英吋寬、1280 像素水平解析度的監視器上，96 像素的水平線長度約一英吋的 9/10。  
  
 變更 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定與變更螢幕解析度不同。 使用 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 縮放比例時，畫面上的實體像素數目會維持不變。 不過，縮放比例會套用至 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的大小和位置。 針對未明確要求不縮放的桌面和應用程式，桌面視窗管理員 (DWM) 會自動執行縮放。  
  
 實際上，當使用者將縮放因數設定為 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]時，畫面上的垂直或水平英吋會增大 25%。 所有維度都會因此調整。 來自畫面上方和左邊緣的應用程式視窗位移會增加 25%。 如果應用程式縮放已啟用，但應用程式不是 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]感知，則視窗大小以及它所包含的所有 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 項目的位移和大小也會以相同比例增加。  
  
> [!NOTE]
>  根據預設，當使用者將[!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]設定為 120 時，DWM 不會針對非 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 感知的應用程式執行縮放，但當 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定為自訂值 144 (含) 以上時就會執行縮放。 不過，使用者可以覆寫此預設行為。  
  
 針對重視畫面座標的應用程式，畫面縮放比例會產生新挑戰。 畫面現在包含兩個座標系統：實體和邏輯。 點的實體座標是來自原點左上方的實際位移 (以像素為單位)。 邏輯座標則是像素本身縮放時，跟著縮放的位移。  
  
 假設您設計的對話方塊在座標 (100, 48) 上有一個按鈕。 當這個對話方塊以預設 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]顯示時，按鈕位在實體座標 (100, 48)。 在 120 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]時，它位在實體座標 (125, 60)。 但邏輯座標在任何 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定時都是相同的：(100, 48)。  
  
 邏輯座標很重要，因為不論 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定為何，它們都會維持作業系統和應用程式的一致行為。 例如，<xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>通常會傳回邏輯座標。 如果您將游標移至對話方塊內的項目上，不論 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定為何，都會傳回相同座標。 如果您在 (100, 100) 繪製控制項，它會繪製到這些邏輯座標上，並在任何 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 設定上佔用相同的相對位置。  
  
<a name="Scaling_in_UI_Automation_Clients"></a>   
## <a name="scaling-in-ui-automation-clients"></a>使用者介面自動化用戶端中的縮放比例  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA#tla_api](../../../includes/tlasharptla-api-md.md)] 不會使用邏輯座標。 下列方法和屬性會傳回實體座標或採用它們做為參數。  
  
-   <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetClickablePoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElement.FromPoint%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>  
  
 根據預設，在非 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 環境中執行的使用者介面自動化用戶端應用程式將無法從這些方法和屬性取得正確結果。 例如，因為游標位置是在邏輯座標中，用戶端無法單純地將這些座標傳遞至 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> ，以取得游標下的項目。 此外，應用程式也將無法在其用戶端區域之外正確放置視窗。  
  
 解決方法分為兩個部分。  
  
1.  第一，讓用戶端應用程式成為 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]感知。 若要執行這項動作，請在啟動時呼叫 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 函式 `SetProcessDPIAware` 。 以 Managed 程式碼的下列宣告，讓這個函式成為可用的。  
  
     [!code-csharp[Highlighter#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/Highlighter/CSharp/NativeMethods.cs#101)]
     [!code-vb[Highlighter#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Highlighter/VisualBasic/NativeMethods.vb#101)]  
  
     這個函式會讓整個處理序成為 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]感知，表示屬於該處理序的所有視窗都是未縮放。 在[螢光筆範例](http://msdn.microsoft.com/library/19ba4577-753e-4efd-92cc-c02ee67c1b69)，比方說，構成反白顯示矩形四個視窗是位在取自實體座標[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，非邏輯座標。 如果這個範例不是 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]感知，就會在桌面的邏輯座標上繪製反白顯示，而在非 96 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)] 環境中，這會造成放置不正確的情況。  
  
2.  若要取得游標座標，請呼叫 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 函式 `GetPhysicalCursorPos`。 下列範例顯示如何宣告及使用這個函式。  
  
     [!code-csharp[UIAClient_snip#185](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#185)]
     [!code-vb[UIAClient_snip#185](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#185)]  
  
> [!CAUTION]
>  請勿使用<xref:System.Windows.Forms.Cursor.Position%2A?displayProperty=nameWithType>。 這個屬性在縮放環境中用戶端視窗之外的行為是未定義的。  
  
 如果您的應用程式與非 [!INCLUDE[TLA2#tla_dpi](../../../includes/tla2sharptla-dpi-md.md)]感知的應用程式執行直接跨處理序通訊，您可能必須使用 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] 函式 `PhysicalToLogicalPoint` 和 `LogicalToPhysicalPoint`，在邏輯與實體座標之間轉換。  
  
## <a name="see-also"></a>請參閱  
 [螢光筆範例](http://msdn.microsoft.com/library/19ba4577-753e-4efd-92cc-c02ee67c1b69)
