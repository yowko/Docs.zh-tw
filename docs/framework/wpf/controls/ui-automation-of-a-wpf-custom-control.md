---
title: WPF 自訂控制項的 UI 自動化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], applying UI automation
- accessibility [WPF], applying to custom controls
- custom controls [WPF], improving accessibility
- UI Automation [WPF], using with custom controls
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
ms.openlocfilehash: 0d663acc195b36fdc95c196f2233ae997fbd9195
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132765"
---
# <a name="ui-automation-of-a-wpf-custom-control"></a>WPF 自訂控制項的 UI 自動化
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)] 提供一個單一的通用介面，可讓自動化用戶端用來檢查或操作各種平台和架構的使用者介面。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 可讓品質保證 (測試) 程式碼和協助工具應用程式 (例如螢幕助讀程式) 檢查使用者介面元素，並模擬從其他程式碼與它們進行的使用者互動。 如需跨所有平台之 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 的相關資訊，請參閱＜協助工具＞。  
  
 本主題說明如何針對在 WPF 應用程式中執行的自訂控制項，實作伺服器端 UI 自動化提供者。 WPF 是透過與使用者介面元素樹狀結構平行的對等自動化物件樹狀結構，來支援 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]。 提供協助工具功能的測試程式碼和應用程式，可以直接使用自動化對等物件 (針對同處理序程式碼)，或透過由 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 提供的一般介面來使用這些物件。  

<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>自動化對等類別  
 WPF 控制項支援[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]透過對等類別衍生自的樹狀結構<xref:System.Windows.Automation.Peers.AutomationPeer>。 依照慣例，對等類別名稱會以控制項類別名稱開始，並以 "AutomationPeer" 結束。 例如，<xref:System.Windows.Automation.Peers.ButtonAutomationPeer>是對等類別<xref:System.Windows.Controls.Button>控制項類別。 對等類別大致上相當於 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 控制項類型，但專屬於 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 元素。 透過 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 介面存取 WPF 應用程式的自動化程式碼並不會直接使用自動化對等，但相同處理序空間中的自動化程式碼則可以直接使用自動化對等。  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>內建自動化對等類別  
 如果元素接受來自使用者的介面活動，或包含螢幕助讀應用程式使用者所需的資訊，便會實作自動化對等類別。 並非所有 WPF 視覺元素都有自動化對等。 實作自動化對等的類別範例包括<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.TextBox>，和<xref:System.Windows.Controls.Label>。 不會實作自動化對等的類別範例包括衍生自類別<xref:System.Windows.Controls.Decorator>，這類<xref:System.Windows.Controls.Border>，並根據類別<xref:System.Windows.Controls.Panel>，例如<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Controls.Canvas>。  
  
 基底<xref:System.Windows.Controls.Control>類別沒有相對應的對等類別。 如果您需要對等類別，以對應至自訂控制項衍生自<xref:System.Windows.Controls.Control>，您應該自訂對等類別衍生自<xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>。  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>衍生對等的安全性考量  
 自動化對等必須在部分信任的環境中執行。 UIAutomationClient 組件中的程式碼並沒有針對在部分信任的環境中執行進行設定，因此自動化對等程式碼不應該參考該組件。 您應該改為使用 UIAutomationTypes 組件中的類別。 例如，您應該使用<xref:System.Windows.Automation.AutomationElementIdentifiers>來自 UIAutomationTypes 組件，其對應至類別<xref:System.Windows.Automation.AutomationElement>UIAutomationClient 組件中的類別。 在自動化對等程式碼中參考 UIAutomationTypes 組件是安全的。  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>對等瀏覽  
 找到之後的自動化對等，同處理序程式碼可以藉由呼叫物件的巡覽對等樹狀結構<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A>和<xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A>方法。 瀏覽[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]控制項中的項目支援的對等實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A>方法。 UI 自動化系統會呼叫此方法來建置控制項內所包含之子元素的樹狀結構，例如清單方塊中的清單項目。 預設值<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=nameWithType>; 方法會周遊視覺化樹狀結構的項目建立的自動化對等樹狀結構。 自訂控制項會覆寫此方法，以將子系元素公開給自動化用戶端，並傳回能傳達資訊或允許使用者互動的元素自動化對等。  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>衍生對等中的自訂  
 所有的類別衍生自<xref:System.Windows.UIElement>並<xref:System.Windows.ContentElement>包含受保護的虛擬方法<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>。 WPF 會呼叫<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>來取得每個控制項的自動化對等物件。 自動化程式碼可以使用對等來取得控制項特性和功能的相關資訊，並模擬互動式使用。 支援自動化的自訂控制項必須覆寫<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>，並傳回衍生自類別的執行個體<xref:System.Windows.Automation.Peers.AutomationPeer>。 例如，如果自訂控制項衍生自<xref:System.Windows.Controls.Primitives.ButtonBase>類別，則所傳回的物件<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>應該衍生自<xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>。  
  
 實作自訂控制項時，您必須從描述您自訂控制項唯一且特定之行為的基底自動化對等類別，覆寫 "Core" 方法。  
  
### <a name="override-oncreateautomationpeer"></a>覆寫 OnCreateAutomationPeer  
 覆寫<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>方法，為您自訂的控制項，讓它傳回您的提供者物件，必須直接或間接衍生自<xref:System.Windows.Automation.Peers.AutomationPeer>。  
  
### <a name="override-getpattern"></a>覆寫 GetPattern  
 自動化對等可簡化伺服器端 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 提供者的部分實作層面，但自訂控制項自動化對等仍須處理模式介面。 非 WPF 提供者，例如對等支援控制項模式所提供的介面中實作<xref:System.Windows.Automation.Provider?displayProperty=nameWithType>命名空間，例如<xref:System.Windows.Automation.Provider.IInvokeProvider>。 控制項模式介面可以由對等本身實作，或是由另一個物件實作。 對等體的實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>傳回支援指定的模式的物件。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 程式碼會呼叫<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>方法，並指定<xref:System.Windows.Automation.Peers.PatternInterface>列舉值。 覆寫<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>會傳回實作指定的模式的物件。 如果您的控制項沒有模式的自訂實作，您可以呼叫基底型別的實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>擷取其實作或 null，如果模式不支援此控制項類型。 比方說，可以設定自訂的 NumericUpDown 控制項的值在範圍內，因此其[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]對等會實作<xref:System.Windows.Automation.Provider.IRangeValueProvider>介面。 下列範例示範如何為對等的<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>方法會覆寫回應<xref:System.Windows.Automation.Peers.PatternInterface.RangeValue?displayProperty=nameWithType>值。  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>方法也可以指定子元素做為模式提供者。 下列程式碼示範如何<xref:System.Windows.Controls.ItemsControl>傳輸捲動模式處理其內部的對等<xref:System.Windows.Controls.ScrollViewer>控制項。  
  
```csharp  
public override object GetPattern(PatternInterface patternInterface)  
{  
    if (patternInterface == PatternInterface.Scroll)  
    {  
        ItemsControl owner = (ItemsControl) base.Owner;  
  
        // ScrollHost is internal to the ItemsControl class  
        if (owner.ScrollHost != null)  
        {  
            AutomationPeer peer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost);  
            if ((peer != null) && (peer is IScrollProvider))  
            {  
                peer.EventsSource = this;  
                return (IScrollProvider) peer;  
            }  
        }  
    }  
    return base.GetPattern(patternInterface);  
}  
```  
  
```vb  
Public Class Class1  
    Public Overrides Function GetPattern(ByVal patternInterface__1 As PatternInterface) As Object  
        If patternInterface1 = PatternInterface.Scroll Then  
            Dim owner As ItemsControl = DirectCast(MyBase.Owner, ItemsControl)  
  
            ' ScrollHost is internal to the ItemsControl class  
            If owner.ScrollHost IsNot Nothing Then  
                Dim peer As AutomationPeer = UIElementAutomationPeer.CreatePeerForElement(owner.ScrollHost)  
                If (peer IsNot Nothing) AndAlso (TypeOf peer Is IScrollProvider) Then  
                    peer.EventsSource = Me  
                    Return DirectCast(peer, IScrollProvider)  
                End If  
            End If  
        End If  
        Return MyBase.GetPattern(patternInterface1)  
    End Function  
End Class  
```  
  
 若要指定模式處理的子元素，此程式碼取得子元素物件、 使用會建立對等<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>方法，會設定<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>目前的對等，新的對等的屬性，並傳回新的對等個體。 設定<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>子元素上會防止子元素不會出現在自動化對等樹狀結構，並將指定子元素所引發的所有事件中指定的控制項來自<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>。 <xref:System.Windows.Controls.ScrollViewer>控制項不會出現在自動化樹狀目錄中，以及它所產生的捲動事件顯示為源自<xref:System.Windows.Controls.ItemsControl>物件。  
  
### <a name="override-core-methods"></a>覆寫 "Core" 方法  
 自動化程式碼會呼叫對等類別的公用方法，來取得控制項的相關資訊。 若要提供您控制項的相關資訊，請在您的控制項實作和由基底自動化對等類別所提供的不同時，覆寫所有名稱以 "Core" 為結尾的方法。 您的控制項必須實作最少<xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A>和<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>方法，如下列範例所示。  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 您實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>藉由傳回描述您的控制項<xref:System.Windows.Automation.ControlType>值。 雖然您可以傳回<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>，您應在如果更加精確地描述您的控制項傳回其中一種更特定的控制項類型。 傳回值<xref:System.Windows.Automation.ControlType.Custom?displayProperty=nameWithType>需要額外的工作，讓提供者實作[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]，和[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]用戶端產品是無法預期控制項結構、 鍵盤互動，以及可能的控制項模式。  
  
 實作<xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A>和<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>方法以指出控制項是否包含資料內容，或可滿足使用者介面 （或兩者） 中的互動式角色。 根據預設，這兩個方法皆會傳回 `true`。 這些設定能改善自動化工具 (例如螢幕助讀程式) 的可用性，這些工具可以使用這些方法來篩選自動化樹狀結構。 如果您<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>子元素對等元素對等的處理方法傳輸模式<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>方法可以傳回 false 表示隱藏元素對等，從自動化樹狀結構。 比方說，在捲動<xref:System.Windows.Controls.ListBox>由<xref:System.Windows.Controls.ScrollViewer>，和的自動化同儕節點<xref:System.Windows.Automation.Peers.PatternInterface.Scroll?displayProperty=nameWithType>會傳回<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>方法<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>相關聯<xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>。因此，<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>方法<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>會傳回`false`，以便<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>不會出現在自動化樹狀目錄中。  
  
 您的自動化對等應該為您的控制項提供適當的預設值。 請注意，參考您控制項的 XAML 可以透過覆寫您的對等實作核心方法包括<xref:System.Windows.Automation.AutomationProperties>屬性。 例如，下列 XAML 會建立有兩個自訂 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)] 屬性的按鈕。  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>實作模式提供者  
 如果擁有的項目直接衍生自明確宣告的自訂提供者所實作的介面<xref:System.Windows.Controls.Control>。 例如，下列程式碼會宣告的對等個體<xref:System.Windows.Controls.Control>實作範圍值。  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 如果擁有控制項是衍生自特定的控制項類型這類<xref:System.Windows.Controls.Primitives.RangeBase>，對等電腦可以衍生自的對等的衍生對等類別。 在此情況下，將對等會衍生自<xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>，其中提供的基底實作<xref:System.Windows.Automation.Provider.IRangeValueProvider>。 下列程式碼顯示這種對等的宣告。  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 如需範例實作，請參閱[具有佈景主題和 UI 自動化支援的 NumericUpDown 自訂控制項範例](https://go.microsoft.com/fwlink/?LinkID=160025)。  
  
### <a name="raise-events"></a>引發事件  
 自動化用戶端可以訂閱自動化事件。 自訂控制項必須將控制藉由呼叫的狀態變更報告<xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>方法。 同樣地，屬性值變更時，呼叫<xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>方法。 下列程式碼示範如何從控制項程式碼內取得對等物件，並呼叫方法以引發事件。 做為最佳化的手段，程式碼會判斷此事件類型是否有任何接聽程式。 只在有接聽程式的情況下引發事件，可以避免不必要的額外負荷並協助保持控制項的反應性。  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>另請參閱

- [UI 自動化概觀](../../ui-automation/ui-automation-overview.md)
- [具有佈景主題和 UI 自動化支援範例的 NumericUpDown 自訂控制項](https://go.microsoft.com/fwlink/?LinkID=160025)
- [伺服器端 UI 自動化提供者實作](../../ui-automation/server-side-ui-automation-provider-implementation.md)
