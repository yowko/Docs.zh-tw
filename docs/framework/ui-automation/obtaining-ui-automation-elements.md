---
title: 取得 UI 自動化項目
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3e700e7e726b5cb71d3b7d863bdb31951aacd885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399196"
---
# <a name="obtaining-ui-automation-elements"></a>取得 UI 自動化項目
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題描述取得 <xref:System.Windows.Automation.AutomationElement> 項目之 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 物件的各種方式。  
  
> [!CAUTION]
>  如果用戶端應用程式可能會嘗試尋找本身使用者介面中的項目，您就必須在個別執行緒上進行所有 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 呼叫。 如需詳細資訊，請參閱 [UI Automation Threading Issues](../../../docs/framework/ui-automation/ui-automation-threading-issues.md)。  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>根項目  
 對於 <xref:System.Windows.Automation.AutomationElement> 物件的所有搜尋都必須有一個開始位置。 這可以是任何項目，包括桌面、應用程式視窗或控制項。  
  
 所有項目會繼承而來，桌面的根項目取自靜態<xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType>屬性。  
  
> [!CAUTION]
>  一般而言，您應該試著取得 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>的直接子系。 如果搜尋子系可能會逐一查看數百或甚至數千個項目，就很有可能會造成堆疊溢位。 如果您嘗試取得較低層級的特定項目，您就應該要從應用程式視窗或較低層級的容器開始搜尋。  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Conditions  
 對於可用來擷取 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目的大部分技術，您都必須指定 <xref:System.Windows.Automation.Condition>，這是一組準則，定義您想要擷取哪些項目。  
  
 最簡單的條件是 <xref:System.Windows.Automation.Condition.TrueCondition>，是一種預先定義的物件，會指定要傳回之搜尋範圍內的所有項目。 <xref:System.Windows.Automation.Condition.FalseCondition>，也就是 <xref:System.Windows.Automation.Condition.TrueCondition>的反向，並不是很有用，原因在於它可能會讓任何項目都無法被找到。  
  
 有三個預先定義的條件可單獨使用，或與其他條件組合使用： <xref:System.Windows.Automation.Automation.ContentViewCondition>、 <xref:System.Windows.Automation.Automation.ControlViewCondition>和 <xref:System.Windows.Automation.Automation.RawViewCondition>。 <xref:System.Windows.Automation.Automation.RawViewCondition>供本身使用，相當於 <xref:System.Windows.Automation.Condition.TrueCondition>，原因在於它不會依其 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> 或 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> 屬性篩選項目。  
  
 其他條件可從一個以上的 <xref:System.Windows.Automation.PropertyCondition> 物件建置，其中每個物件都會指定屬性值。 例如， <xref:System.Windows.Automation.PropertyCondition> 可能指定該項目是否已啟用，或者它是否支援特定的控制項模式。  
  
 條件可以使用布林邏輯加以組合，方法是建構 <xref:System.Windows.Automation.AndCondition>、 <xref:System.Windows.Automation.OrCondition>和 <xref:System.Windows.Automation.NotCondition>類型的物件。  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>搜尋範圍  
 使用 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 或 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> 完成的搜尋必須具備範圍以及開始位置。  
  
 此範圍定義要搜尋之開始位置周圍的空間。 這可能包含項目本身，及該項目的同層級、父系、祖系、直接子系和子系。  
  
 此搜尋範圍由 <xref:System.Windows.Automation.TreeScope> 列舉值的位元組合所定義。  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>尋找已知的項目  
 若要尋找已知的項目，且該項目由其 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>或某些其他屬性或屬性組合所識別，則使用 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> 方法最為容易。 如果要搜尋的項目是應用程式視窗，則搜尋開始點可以是 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>。  
  
 用這種方式在自動化測試情節中尋找 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 項目最好用。  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>在子樹狀結構中尋找項目  
 若要尋找符合與已知項目相關之特定準則的所有項目，您可以使用 <xref:System.Windows.Automation.AutomationElement.FindAll%2A>。 例如，您或許可以使用這個方法，從清單或功能表上擷取清單項目或功能表項目，或識別在對話方塊中的所有控制項。  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>逐一查看子樹狀結構  
 如果您事先不知道您的用戶端可搭配使用的應用程式，您可以建構所需所有項目的子樹狀結構，方法是使用 <xref:System.Windows.Automation.TreeWalker> 類別。 您的應用程式可能會執行這項操作以回應焦點變更的事件；也就是當應用程式或控制項收到輸入的焦點時，使用者介面自動化用戶端會檢查子系，也可能檢查已取得焦點之項目的所有子系。  
  
 而可使用 <xref:System.Windows.Automation.TreeWalker> 的另一種方式為識別項目的祖系。 例如，您可以向上查看樹狀結構來識別控制項的父視窗。  
  
 您可以建立此類別的物件 (藉由傳遞 <xref:System.Windows.Automation.TreeWalker> 定義所需項目) 來使用 <xref:System.Windows.Automation.Condition>，或使用下列其中一種預先定義的物件，該物件定義為 <xref:System.Windows.Automation.TreeWalker>的欄位。  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|只尋找其 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> 屬性是 `true`的項目。|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|只尋找其 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> 屬性是 `true`的項目。|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|尋找所有項目。|  
  
 在您取得 <xref:System.Windows.Automation.TreeWalker>之後，用法就非常簡單。 只要呼叫 `Get` 方法在子樹狀結構的項目之間瀏覽即可。  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> 方法可用來瀏覽至項目，該項目位於另一個不屬於該檢視之項目的子樹狀結構中。 例如，假設您已使用 <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>建立子樹狀結構檢視。 您的應用程式接著會收到通知，指出捲軸已接收輸入焦點。 因為捲軸不是內容項目，所以不會出現在子樹狀結構檢視中。 不過，您可以將代表此捲軸的 <xref:System.Windows.Automation.AutomationElement> 傳遞至 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> ，並擷取內容檢視中最接近的祖系。  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>擷取項目的其他方式  
 除了搜尋和瀏覽以外，您也可以用下列方式擷取 <xref:System.Windows.Automation.AutomationElement> 。  
  
### <a name="from-an-event"></a>從事件擷取  
 當您的應用程式收到 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 事件時，傳遞至事件處理常式的來源物件是 <xref:System.Windows.Automation.AutomationElement>。 例如，如果您已訂閱焦點變更事件，則傳遞給 <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> 的來源是接收此焦點的項目。  
  
 如需詳細資訊，請參閱 [Subscribe to UI Automation Events](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)。  
  
### <a name="from-a-point"></a>從點擷取  
 如果您有螢幕座標 (例如滑鼠指標位置)，您就可以使用靜態 <xref:System.Windows.Automation.AutomationElement> 方法來擷取 <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> 。  
  
### <a name="from-a-window-handle"></a>從視窗控制代碼擷取  
 若要從 HWND 擷取 <xref:System.Windows.Automation.AutomationElement> ，請使用靜態 <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> 方法。  
  
### <a name="from-the-focused-control"></a>從取得焦點的控制項擷取  
 您可以從靜態 <xref:System.Windows.Automation.AutomationElement> 屬性擷取 <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> ，其代表取得焦點的控制項。  
  
## <a name="see-also"></a>另請參閱  
 [根據屬性條件尋找 UI 自動化項目](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [使用 TreeWalker 導覽 UI 自動化項目](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [UI 自動化樹狀目錄概觀](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
