---
title: "WPF 自訂控制項的 UI 自動化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "套用 UI 自動化的自訂控制項 [WPF]"
  - "協助工具 [WPF]，將套用到自訂控制項"
  - "自訂控制項 [WPF] 改善可及性"
  - "使用自訂控制項的 UI 自動化 [WPF]"
ms.assetid: 47b310fc-fbd5-4ce2-a606-22d04c6d4911
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# WPF 自訂控制項的 UI 自動化
[!INCLUDE[TLA#tla_uiautomation](../../../../includes/tlasharptla-uiautomation-md.md)]提供一個單一的通用介面，該用戶端可用來檢查或操作的各種不同的平台和架構使用者介面的自動化。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]可讓品質保證 （測試） 的程式碼並檢查使用者介面項目，並模擬它們與其他程式碼的使用者互動的螢幕助讀程式之類的協助工具應用程式。 如需有關資訊[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]跨所有平台，請參閱協助工具。  
  
 本主題說明如何實作伺服器端 UI 自動化提供者會在 WPF 應用程式中執行的自訂控制項。 WPF 支援[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]透過平行設計的使用者介面項目樹狀結構的對等的 automation 物件的樹狀結構。 測試程式碼和應用程式，提供協助工具功能可用於自動化對等物件直接 （同處理序的程式碼） 或透過提供通用介面[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]。  
  
 
  
<a name="AutomationPeerClasses"></a>   
## <a name="automation-peer-classes"></a>自動化對等類別  
 WPF 控制項支援[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]透過對等類別衍生自的樹狀結構<xref:System.Windows.Automation.Peers.AutomationPeer>。 依照慣例，對等類別名稱控制項類別名稱的開頭和結尾 「 AutomationPeer 」。 例如， <xref:System.Windows.Automation.Peers.ButtonAutomationPeer>是對等類別<xref:System.Windows.Controls.Button>控制類別。 對等類別的大致上相當於[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]控制型別，但專屬於[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]項目。 存取透過 WPF 應用程式的自動化程式碼[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]介面不會直接使用自動化對等物件，但在相同的處理序空間中的自動化程式碼可以直接使用自動化對等物件。  
  
<a name="BuiltInAutomationPeerClasses"></a>   
## <a name="built-in-automation-peer-classes"></a>內建自動化對等類別  
 如果他們接受來自使用者的介面活動，或包含使用者的螢幕助讀程式的應用程式所需的資訊項目會實作自動化對等類別。 並非所有的 WPF 視覺化項目有自動化對等物件。 實作自動化對等物件的類別的範例包括<xref:System.Windows.Controls.Button>，<xref:System.Windows.Controls.TextBox>，和<xref:System.Windows.Controls.Label>。 不會實作自動化對等物件之類別的範例是衍生自類別<xref:System.Windows.Controls.Decorator>，例如<xref:System.Windows.Controls.Border>，以及根據類別<xref:System.Windows.Controls.Panel>，例如<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Controls.Canvas>。  
  
 基底<xref:System.Windows.Controls.Control>類別沒有對應的對等類別。 如果您需要以自訂控制項衍生自對應的對等類別<xref:System.Windows.Controls.Control>，您應該將自訂對等類別衍生自<xref:System.Windows.Automation.Peers.FrameworkElementAutomationPeer>。  
  
<a name="SecurityConsiderations"></a>   
## <a name="security-considerations-for-derived-peers"></a>在衍生的對等的安全性考量  
 自動化對等物件必須在部分信任環境中執行。 UIAutomationClient 組件中的程式碼未設定為在部分信任環境中，執行和自動化等程式碼不應該參考該組件。 相反地，您應該使用類別 UIAutomationTypes 組件中。 例如，您應該使用<xref:System.Windows.Automation.AutomationElementIdentifiers> UIAutomationTypes 組件，對應於從類別<xref:System.Windows.Automation.AutomationElement> UIAutomationClient 組件中的類別。 它是安全參考 UIAutomationTypes 組件自動化對等程式碼中。  
  
<a name="PeerNavigation"></a>   
## <a name="peer-navigation"></a>對等物件巡覽  
 之後尋找自動化對等，同處理序程式碼可以藉由呼叫物件的巡覽樹狀目錄中對等<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildren%2A>和<xref:System.Windows.Automation.Peers.AutomationPeer.GetParent%2A>方法。 在瀏覽[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]控制項中的項目支援的對等的實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetChildrenCore%2A>方法。 UI 自動化系統會呼叫這個方法來建置樹狀結構的控制項; 所含的子元素例如，清單中的項目清單方塊。 預設<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetChildrenCore%2A?displayProperty=fullName>方法會周遊項目建立自動化對等物件的樹狀結構的視覺化樹狀結構。 自訂控制項覆寫這個方法，以公開至 automation 用戶端傳回的項目來傳達資訊或允許使用者互動的自動化對等物件的子系項目。  
  
<a name="Customizations"></a>   
## <a name="customizations-in-a-derived-peer"></a>在衍生的對等的自訂項目  
 所有的類別衍生自<xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>包含受保護的虛擬方法<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>。 WPF 呼叫<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>取得每個控制項的自動化對等物件。 取得控制項的特性和功能的相關資訊，並模擬互動使用自動化程式碼可以使用對等。 支援自動化的自訂控制項必須覆寫<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A> ，並傳回衍生自類別的執行個體<xref:System.Windows.Automation.Peers.AutomationPeer>。 例如，如果自訂控制項是衍生自<xref:System.Windows.Controls.Primitives.ButtonBase>類別，則所傳回的物件<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>應衍生自<xref:System.Windows.Automation.Peers.ButtonBaseAutomationPeer>。  
  
 在實作自訂控制項，您必須覆寫來自基底自動化對等類別描述行為唯一，且您的自訂控制項的 「 核心 」 方法。  
  
### <a name="override-oncreateautomationpeer"></a>覆寫 OnCreateAutomationPeer  
 覆寫<xref:System.Windows.UIElement.OnCreateAutomationPeer%2A>方法為您自訂的控制項，讓它傳回您的提供者物件，必須直接或間接衍生自<xref:System.Windows.Automation.Peers.AutomationPeer>。  
  
### <a name="override-getpattern"></a>覆寫 GetPattern  
 自動化對等物件簡化伺服器端的一些實作層面[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]提供者，但自訂控制項自動化對等物件仍必須處理模式介面。 非 WPF 提供者，例如對等支援藉由提供實作的介面中的控制項模式<xref:System.Windows.Automation.Provider?displayProperty=fullName>命名空間，例如<xref:System.Windows.Automation.Provider.IInvokeProvider>。 控制項模式介面可以實作本身的對等或另一個物件。 對等的實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>傳回的物件，支援指定的模式。 [!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]程式碼會呼叫<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>方法，並指定<xref:System.Windows.Automation.Peers.PatternInterface>列舉值。 覆寫<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>應該會傳回實作指定之的模式的物件。 如果您的控制項並沒有一種模式的自訂實作，您可以呼叫基底型別的實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>擷取其實作 」 或 「 null，如果模式不支援此控制項類型。 自訂數值上下按鈕控制項，例如設的值在範圍內，因此其[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]對等會實作<xref:System.Windows.Automation.Provider.IRangeValueProvider>介面。 下列範例將示範如何為對等的<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>回應會覆寫方法<xref:System.Windows.Automation.Peers.PatternInterface?displayProperty=fullName>值。  
  
 [!code-csharp[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#getpattern)]
 [!code-vb[CustomControlNumericUpDown#GetPattern](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#getpattern)]  
  
 A <xref:System.Windows.Automation.Peers.UIElementAutomationPeer.GetPattern%2A>方法也可以指定子元素做為模式提供者。 下列程式碼顯示如何<xref:System.Windows.Controls.ItemsControl>傳輸捲動模式處理其內部的對等電腦<xref:System.Windows.Controls.ScrollViewer>控制項。  
  
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
  
 若要指定模式處理的子元素，此程式碼取得子元素的物件、 使用會建立對等<xref:System.Windows.Automation.Peers.UIElementAutomationPeer.CreatePeerForElement%2A>方法，會設定<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>目前對等新的對等的屬性，並傳回新的對等。 設定<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>子元素上防止子元素出現在自動化等樹狀目錄中，並且將所有子元素所引發的事件中指定的控制項所源自<xref:System.Windows.Automation.Peers.AutomationPeer.EventsSource%2A>。 <xref:System.Windows.Controls.ScrollViewer>控制項未出現在自動化樹狀目錄中，以及它所產生的捲動事件看起來像是來自<xref:System.Windows.Controls.ItemsControl>物件。  
  
### <a name="override-core-methods"></a>覆寫 「 核心 」 方法  
 自動化程式碼呼叫的對等類別的公用方法來取得控制項的相關資訊。 若要提供控制項的相關資訊，請覆寫其名稱結尾 「 核心 」 時控制項實作不同於基底自動化對等類別所提供的每個方法。 至少，您的控制項必須實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetClassNameCore%2A>和<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>方法，如下列範例所示。  
  
 [!code-csharp[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#coreoverrides)]
 [!code-vb[CustomControlNumericUpDown#CoreOverrides](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#coreoverrides)]  
  
 實作<xref:System.Windows.Automation.Peers.AutomationPeer.GetAutomationControlTypeCore%2A>描述您的控制項，藉由傳回<xref:System.Windows.Automation.ControlType>值。 雖然您可以傳回<xref:System.Windows.Automation.ControlType.Custom?displayProperty=fullName>，它會精確地描述您的控制項，如果您應該傳回更特定的控制項類型的其中一個。 傳回值為<xref:System.Windows.Automation.ControlType.Custom?displayProperty=fullName>需要額外的工作，讓提供者實作[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]，和[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]用戶端產品是無法預期的控制結構、 鍵盤互動和可能的控制模式。  
  
 實作<xref:System.Windows.Automation.Peers.AutomationPeer.IsContentElementCore%2A>和<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>方法以指出控制項是否包含資料內容，或可滿足以互動式角色的使用者介面 （或兩者）。 根據預設，這兩種方法會傳回`true`。 這些設定可以改善自動化工具，例如螢幕助讀程式，可能會使用這些方法來篩選自動化樹狀目錄的可用性。 如果您<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>子元素對等的子元素對等的處理方法的傳輸模式<xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>方法會傳回 false 表示隱藏從自動化樹狀目錄的子元素對等。 比方說，在中捲動<xref:System.Windows.Controls.ListBox>由<xref:System.Windows.Controls.ScrollViewer>，並自動對等<xref:System.Windows.Automation.Peers.PatternInterface?displayProperty=fullName>由<xref:System.Windows.Automation.Peers.AutomationPeer.GetPattern%2A>方法<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>相關聯<xref:System.Windows.Automation.Peers.ListBoxAutomationPeer>。因此， <xref:System.Windows.Automation.Peers.AutomationPeer.IsControlElementCore%2A>方法<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>傳回`false`，好讓<xref:System.Windows.Automation.Peers.ScrollViewerAutomationPeer>不會出現在自動化樹狀目錄中。  
  
 自動化等應該提供適當的預設值為您的控制項。 請注意，參考您的控制項的 XAML 可以藉由覆寫您對等方法的實作核心<xref:System.Windows.Automation.AutomationProperties>屬性。 例如，下列 XAML 會建立具有兩個自訂按鈕[!INCLUDE[TLA2#tla_uiautomation](../../../../includes/tla2sharptla-uiautomation-md.md)]屬性。  
  
```xaml  
<Button AutomationProperties.Name="Special"   
    AutomationProperties.HelpText="This is a special button."/>  
```  
  
### <a name="implement-pattern-providers"></a>實作模式提供者  
 如果擁有的項目直接衍生自明確宣告的自訂提供者所實作之介面<xref:System.Windows.Controls.Control>。 例如，下列程式碼會宣告的對等<xref:System.Windows.Controls.Control>實作範圍值。  
  
```csharp  
public class RangePeer1 : FrameworkElementAutomationPeer, IRangeValueProvider { }  
```  
  
```vb  
Public Class RangePeer1  
    Inherits FrameworkElementAutomationPeer  
    Implements IRangeValueProvider  
End Class  
```  
  
 如果擁有的控制項是衍生自特定類型的控制項例如<xref:System.Windows.Controls.Primitives.RangeBase>，對等可以從對等衍生的對等類別。 在此情況下，對等會衍生自<xref:System.Windows.Automation.Peers.RangeBaseAutomationPeer>，提供的基底實作<xref:System.Windows.Automation.Provider.IRangeValueProvider>。 下列程式碼顯示這種對等的宣告。  
  
```csharp  
public class RangePeer2 : RangeBaseAutomationPeer { }  
```  
  
```vb  
Public Class RangePeer2  
    Inherits RangeBaseAutomationPeer  
End Class  
```  
  
 範例實作，請參閱[NumericUpDown 自訂控制項搭配主題和 UI 自動化支援範例](http://go.microsoft.com/fwlink/?LinkID=160025)。  
  
### <a name="raise-events"></a>引發事件  
 Automation 用戶端可以自動化事件訂閱。 自訂控制項必須報告變更以控制狀態，藉由呼叫<xref:System.Windows.Automation.Peers.AutomationPeer.RaiseAutomationEvent%2A>方法。 同樣地，當屬性值變更時呼叫<xref:System.Windows.Automation.Peers.AutomationPeer.RaisePropertyChangedEvent%2A>方法。 下列程式碼示範如何取得控制項的程式碼中的對等物件，呼叫方法來引發事件。 因為最佳化因素，程式碼會判斷是否有任何的接聽程式，這個事件類型。 引發事件，只有在接聽程式時才可避免不必要的額外負荷，並協助保持回應狀態的控制項。  
  
 [!code-csharp[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/NumericUpDown.cs#raiseeventfromcontrol)]
 [!code-vb[CustomControlNumericUpDown#RaiseEventFromControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/numericupdown.vb#raiseeventfromcontrol)]  
  
## <a name="see-also"></a>另請參閱  
 [UI 自動化概觀](../../../../docs/framework/ui-automation/ui-automation-overview.md)   
 [NumericUpDown 自訂控制項搭配主題和 UI 自動化支援範例](http://go.microsoft.com/fwlink/?LinkID=160025)   
 [伺服器端 UI 自動化提供者實作](../../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)