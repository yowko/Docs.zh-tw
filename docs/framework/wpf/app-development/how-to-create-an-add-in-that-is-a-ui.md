---
title: "如何：建立本身為 UI 的增益集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "建立屬於 UI 的增益集 [WPF]"
  - "增益集 [WPF] 中 UI"
  - "建立 UI 增益集 [WPF]"
  - "UI 增益集 [WPF] 建立"
  - "實作 UI 增益集 [WPF]"
  - "建立增益集管線區段 [WPF]"
ms.assetid: 86375525-282b-4039-8352-8680051a10ea
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：建立本身為 UI 的增益集
\<?xml version="1.0" encoding="utf-8"?>
\<developerHowToDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>這個範例示範如何建立增益集是<token>TLA #tla_wpf</token> <token>TLA #tla_ui</token>這由<token>TLA&#2;tla_wpf</token>獨立應用程式。</para>
    <para>增益集是<token>TLA&#2;tla_ui</token>也就是<token>TLA&#2;tla_wpf</token>使用者控制項。使用者控制項的內容是單一按鈕，按一下時，會顯示訊息方塊。<token>TLA&#2;tla_wpf</token>獨立應用程式裝載增益集<token>TLA&#2;tla_ui</token>作為主應用程式視窗的內容。</para>
    <para>
      <embeddedLabel>必要條件</embeddedLabel>
    </para>
    <para>本範例強調<token>TLA&#2;tla_wpf</token>延伸<token>dnprdnshort</token>增益集模型可啟用此案例中，並假設下列︰</para>
    <list class="bullet">
      <listItem>
        <para>的知識<token>dnprdnshort</token>增益集模型，包括管線、 增益集和主應用程式開發。如果您不熟悉這些概念，請參閱\<legacyLink xlink:href="8dd45b02-7218-40f9-857d-40d7b98b850b">增益集和擴充性</legacyLink>。示範實作管線、 增益集，和主應用程式的教學課程，請參閱\<legacyLink xlink:href="694a33c5-a040-450d-aed5-ac49fc88ce61">逐步解說︰ 建立可延伸應用程式</legacyLink>。</para>
      </listItem> 
      <listItem>
        <para>的知識<token>TLA&#2;tla_wpf</token>延伸<token>dnprdnshort</token>增益集模型，可以在這裡找到︰ \<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">WPF 增益集概觀</link>。</para>
      </listItem> 
    </list> 
  </introduction> 
  <codeExample> 
    <legacy> 
      <content>
        <para>建立是<token>TLA&#2;tla_wpf</token> <token>TLA&#2;tla_ui</token>每個管線區段、 增益集，和主應用程式需要特定的程式碼。</para>
        <para> 
          <token>autoOutline</token>
        </para>
      </content>
      <sections>
        <section address="Contract">
          <title>實作合約管線區段</title>
          <content>
            <para>增益集時<token>TLA&#2;tla_ui</token>，增益集的合約必須實作<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>。在範例中， <codeInline>IWPFAddInContract</codeInline>實作<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>，如下列程式碼所示。</para>
            <code language="c#">using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // AddInContractAttribute

namespace Contracts
{
    /// &lt;summary&gt;
    /// Defines the services that an add-in will provide to a host application.
    /// In this case, the add-in is a UI.
    /// &lt;/summary&gt;
    [AddInContract]
    public interface IWPFAddInContract : INativeHandleContract {}
}</code>
          <code language="vb">Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' AddInContractAttribute

Namespace Contracts
    ''' &lt;summary&gt;
    ''' Defines the services that an add-in will provide to a host application.
    ''' In this case, the add-in is a UI.
    ''' &lt;/summary&gt;
    &lt;AddInContract&gt;
    Public Interface IWPFAddInContract
        Inherits INativeHandleContract
        Inherits IContract
    End Interface
End Namespace</code></content>
        </section>
        <section address="AddInViewPipeline">
          <title>實作增益集檢視管線區段</title>
          <content>
            <para>由於增益集當做實作的子類別<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>類型、 增益集檢視表也必須子類別化<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>。下列程式碼顯示增益集檢視的合約，實作為<codeInline>WPFAddInView</codeInline>類別</para>
            <code language="c#">using System.AddIn.Pipeline; // AddInBaseAttribute
using System.Windows.Controls; // UserControl

namespace AddInViews
{
    /// &lt;summary&gt;
    /// Defines the add-in's view of the contract.
    /// &lt;/summary&gt;
    [AddInBase]
    public class WPFAddInView : UserControl { }
}</code> 
          <code language="vb">Imports System.AddIn.Pipeline ' AddInBaseAttribute
Imports System.Windows.Controls ' UserControl

Namespace AddInViews
    ''' &lt;summary&gt;
    ''' Defines the add-in's view of the contract.
    ''' &lt;/summary&gt;
    &lt;AddInBase&gt;
    Public Class WPFAddInView
        Inherits UserControl
    End Class
End Namespace</code> 
            <para>，增益集檢視衍生自<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.UserControl</codeEntityReference>。因此，增益集<token>TLA&#2;tla_ui</token>也應該衍生自<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.UserControl</codeEntityReference>。</para>
          </content>
        </section>
        <section address="AddInSideAdapter">
          <title>實作 Add-In-Side 配接器管線區段</title>
          <content>
            <para>合約時<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>，增益集是<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference> （如同增益集檢視管線區段所指定）。因此， <codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>必須轉換成<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>之前跨越隔離界限。這項工作由增益集端配接器呼叫<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>，如下列程式碼所示。</para>
            <code language="c#">using System; // IntPtr
using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // AddInAdapterAttribute, FrameworkElementAdapters, ContractBase
using System.Security.Permissions;

using AddInViews; // WPFAddInView
using Contracts; // IWPFAddInContract

namespace AddInSideAdapters
{
    /// &lt;summary&gt;
    /// Adapts the add-in's view of the contract to the add-in contract
    /// &lt;/summary&gt;
    [AddInAdapter]
    public class WPFAddIn_ViewToContractAddInSideAdapter : ContractBase, IWPFAddInContract
    {
        WPFAddInView wpfAddInView;

        public WPFAddIn_ViewToContractAddInSideAdapter(WPFAddInView wpfAddInView)
        {
            // Adapt the add-in view of the contract (WPFAddInView) 
            // to the contract (IWPFAddInContract)
            this.wpfAddInView = wpfAddInView;
        }

        /// &lt;summary&gt;
        /// ContractBase.QueryContract must be overridden to:
        /// * Safely return a window handle for an add-in UI to the host 
        ///   application's application.
        /// * Enable tabbing between host application UI and add-in UI, in the
        ///   "add-in is a UI" scenario.
        /// &lt;/summary&gt;
        public override IContract QueryContract(string contractIdentifier)
        {
            if (contractIdentifier.Equals(typeof(INativeHandleContract).AssemblyQualifiedName))
            {
                return FrameworkElementAdapters.ViewToContractAdapter(this.wpfAddInView);
            }

            return base.QueryContract(contractIdentifier);
        }

        /// &lt;summary&gt;
        /// GetHandle is called by the WPF add-in model from the host application's 
        /// application domain to to get the window handle for an add-in UI from the 
        /// add-in's application domain. GetHandle is called if a window handle isn't 
        /// returned by other means ie overriding ContractBase.QueryContract, 
        /// as shown above.
        /// NOTE: This method requires UnmanagedCodePermission to be called 
        ///       (full-trust by default), to prevent illegal window handle
        ///       access in partially trusted scenarios. If the add-in could
        ///       run in a partially trusted application domain 
        ///       (eg AddInSecurityLevel.Internet), you can safely return a window
        ///       handle by overriding ContractBase.QueryContract, as shown above.
        /// &lt;/summary&gt;
        [SecurityPermissionAttribute(SecurityAction.Demand, Flags = SecurityPermissionFlag.UnmanagedCode)]
        public IntPtr GetHandle()
        {
            return FrameworkElementAdapters.ViewToContractAdapter(this.wpfAddInView).GetHandle();
        }
    }
}</code> 
          <code language="vb">Imports System ' IntPtr
Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' AddInAdapterAttribute, FrameworkElementAdapters, ContractBase
Imports System.Security.Permissions

Imports AddInViews ' WPFAddInView
Imports Contracts ' IWPFAddInContract

Namespace AddInSideAdapters
    ''' &lt;summary&gt;
    ''' Adapts the add-in's view of the contract to the add-in contract
    ''' &lt;/summary&gt;
    &lt;AddInAdapter&gt;
    Public Class WPFAddIn_ViewToContractAddInSideAdapter
        Inherits ContractBase
        Implements IWPFAddInContract

        Private wpfAddInView As WPFAddInView

        Public Sub New(ByVal wpfAddInView As WPFAddInView)
            ' Adapt the add-in view of the contract (WPFAddInView) 
            ' to the contract (IWPFAddInContract)
            Me.wpfAddInView = wpfAddInView
        End Sub

        ''' &lt;summary&gt;
        ''' ContractBase.QueryContract must be overridden to:
        ''' * Safely return a window handle for an add-in UI to the host 
        '''   application's application.
        ''' * Enable tabbing between host application UI and add-in UI, in the
        '''   "add-in is a UI" scenario.
        ''' &lt;/summary&gt;
        Public Overrides Function QueryContract(ByVal contractIdentifier As String) As IContract
            If contractIdentifier.Equals(GetType(INativeHandleContract).AssemblyQualifiedName) Then
                Return FrameworkElementAdapters.ViewToContractAdapter(Me.wpfAddInView)
            End If

            Return MyBase.QueryContract(contractIdentifier)
        End Function

        ''' &lt;summary&gt;
        ''' GetHandle is called by the WPF add-in model from the host application's 
        ''' application domain to to get the window handle for an add-in UI from the 
        ''' add-in's application domain. GetHandle is called if a window handle isn't 
        ''' returned by other means ie overriding ContractBase.QueryContract, 
        ''' as shown above.
        ''' NOTE: This method requires UnmanagedCodePermission to be called 
        '''       (full-trust by default), to prevent illegal window handle
        '''       access in partially trusted scenarios. If the add-in could
        '''       run in a partially trusted application domain 
        '''       (eg AddInSecurityLevel.Internet), you can safely return a window
        '''       handle by overriding ContractBase.QueryContract, as shown above.
        ''' &lt;/summary&gt;
        &lt;SecurityPermissionAttribute(SecurityAction.Demand, Flags:=SecurityPermissionFlag.UnmanagedCode)&gt;
        Public Function GetHandle() As IntPtr Implements INativeHandleContract.GetHandle
            Return FrameworkElementAdapters.ViewToContractAdapter(Me.wpfAddInView).GetHandle()
        End Function

    End Class
End Namespace</code>
            <para>在增益集模型，增益集傳回<token>TLA&#2;tla_ui</token> (請參閱\<link xlink:href="57f274b7-4c66-4b72-92eb-81939a393776">How to︰ 建立增益集，會傳回 UI</link>)，增益集配接器轉換<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>至<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>藉由呼叫<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>。<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>必須也來呼叫此模型中，不過您還是必須實作的方法要撰寫程式碼來呼叫它。您可以覆寫<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>和實作程式碼以呼叫<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ViewToContractAdapter(System.Windows.FrameworkElement)</codeEntityReference>如果正在呼叫的程式碼<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>預期<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>。在此情況下，呼叫端會涵蓋後續小節中的主應用程式端配接器。</para>
            <alert class="note">
              <para>您還必須覆寫<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>在主應用程式間啟用定位處理此模型中<token>TLA&#2;tla_ui</token>和增益集<token>TLA&#2;tla_ui</token>。如需詳細資訊，請參閱 \< WPF 增益集限制 > 中\<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">WPF 增益集概觀</link>。</para>
            </alert>
            <para>因為增益集端配接器會實作衍生自介面<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>，您還需要實作<codeEntityReference autoUpgrade="true">M:System.AddIn.Contract.INativeHandleContract.GetHandle</codeEntityReference>，但是會忽略此項時<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>會覆寫。</para>
          </content>
        </section>
        <section address="HostViewPipeline">
          <title>實作主機檢視管線區段</title>
          <content>
            <para>在此模型中，主應用程式通常必須要有 [主機] 檢視是<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>子類別。主機端配接器必須轉換<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>至<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>之後<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>跨越隔離界限。因為方法不呼叫在主應用程式，以取得<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>，主應用程式檢視必須"return" <codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>由包含它。因此，主應用程式檢視必須衍生自的子類別<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>可以包含其他<token>TLA&#2;tla_ui #plural</token>，例如<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.UserControl</codeEntityReference>。下列程式碼會顯示 [主機] 檢視，做為實作的合約， <codeInline>WPFAddInHostView</codeInline>類別。</para>
            <code language="c#">using System.Windows.Controls; // UserControl

namespace HostViews
{
    /// &lt;summary&gt;
    /// Defines the host's view of the add-in
    /// &lt;/summary&gt;
    public class WPFAddInHostView : UserControl { }
}</code>
          <code language="vb">Imports System.Windows.Controls ' UserControl

Namespace HostViews
    ''' &lt;summary&gt;
    ''' Defines the host's view of the add-in
    ''' &lt;/summary&gt;
    Public Class WPFAddInHostView
        Inherits UserControl
    End Class
End Namespace</code>
          </content>
        </section>
        <section address="HostSideAdapter">
          <title>執行主應用程式端配接器管線區段</title>
          <content>
            <para>合約時<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>，主應用程式必須要有<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.UserControl</codeEntityReference> （如 [主機] 檢視所指定）。因此， <codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>必須轉換成<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>之後跨越隔離界限之前設定為 [主機] 檢視的內容, (衍生自<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.UserControl</codeEntityReference>)。</para>
            <para>這項工作由主應用程式端配接器，如下列程式碼所示。</para> 
            <code language="c#">using System.AddIn.Contract; // INativeHandleContract
using System.AddIn.Pipeline; // HostAdapterAttribute, FrameworkElementAdapters, ContractHandle
using System.Windows; // FrameworkElement

using Contracts; // IWPFAddInContract
using HostViews; // WPFAddInHostView

namespace HostSideAdapters
{
    /// &lt;summary&gt;
    /// Adapts the add-in contract to the host's view of the add-in
    /// &lt;/summary&gt;
    [HostAdapter]
    public class WPFAddIn_ContractToViewHostSideAdapter : WPFAddInHostView
    {
        IWPFAddInContract wpfAddInContract;
        ContractHandle wpfAddInContractHandle;

        public WPFAddIn_ContractToViewHostSideAdapter(IWPFAddInContract wpfAddInContract)
        {
            // Adapt the contract (IWPFAddInContract) to the host application's
            // view of the contract (WPFAddInHostView)
            this.wpfAddInContract = wpfAddInContract;

            // Prevent the reference to the contract from being released while the
            // host application uses the add-in
            this.wpfAddInContractHandle = new ContractHandle(wpfAddInContract);

            // Convert the INativeHandleContract for the add-in UI that was passed 
            // from the add-in side of the isolation boundary to a FrameworkElement
            string aqn = typeof(INativeHandleContract).AssemblyQualifiedName;
            INativeHandleContract inhc = (INativeHandleContract)wpfAddInContract.QueryContract(aqn);
            FrameworkElement fe = (FrameworkElement)FrameworkElementAdapters.ContractToViewAdapter(inhc);

            // Add FrameworkElement (which displays the UI provided by the add-in) as
            // content of the view (a UserControl)
            this.Content = fe;
        }
    }
}</code> 
          <code language="vb">Imports System.AddIn.Contract ' INativeHandleContract
Imports System.AddIn.Pipeline ' HostAdapterAttribute, FrameworkElementAdapters, ContractHandle
Imports System.Windows ' FrameworkElement

Imports Contracts ' IWPFAddInContract
Imports HostViews ' WPFAddInHostView

Namespace HostSideAdapters
    ''' &lt;summary&gt;
    ''' Adapts the add-in contract to the host's view of the add-in
    ''' &lt;/summary&gt;
    &lt;HostAdapter&gt;
    Public Class WPFAddIn_ContractToViewHostSideAdapter
        Inherits WPFAddInHostView
        Private wpfAddInContract As IWPFAddInContract
        Private wpfAddInContractHandle As ContractHandle

        Public Sub New(ByVal wpfAddInContract As IWPFAddInContract)
            ' Adapt the contract (IWPFAddInContract) to the host application's
            ' view of the contract (WPFAddInHostView)
            Me.wpfAddInContract = wpfAddInContract

            ' Prevent the reference to the contract from being released while the
            ' host application uses the add-in
            Me.wpfAddInContractHandle = New ContractHandle(wpfAddInContract)

            ' Convert the INativeHandleContract for the add-in UI that was passed 
            ' from the add-in side of the isolation boundary to a FrameworkElement
            Dim aqn As String = GetType(INativeHandleContract).AssemblyQualifiedName
            Dim inhc As INativeHandleContract = CType(wpfAddInContract.QueryContract(aqn), INativeHandleContract)
            Dim fe As FrameworkElement = CType(FrameworkElementAdapters.ContractToViewAdapter(inhc), FrameworkElement)

            ' Add FrameworkElement (which displays the UI provided by the add-in) as
            ' content of the view (a UserControl)
            Me.Content = fe
        End Sub
    End Class
End Namespace</code>
            <para>如您所見，主應用程式端配接器取得<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>藉由呼叫增益集端配接器的<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.ContractBase.QueryContract(System.String)</codeEntityReference>方法 (這是點位置<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>跨越隔離界限)。</para>
            <para>主機端配接器接著將轉換<codeEntityReference autoUpgrade="true">T:System.AddIn.Contract.INativeHandleContract</codeEntityReference>至<codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>藉由呼叫<codeEntityReference autoUpgrade="true">M:System.AddIn.Pipeline.FrameworkElementAdapters.ContractToViewAdapter(System.AddIn.Contract.INativeHandleContract)</codeEntityReference>。最後， <codeEntityReference autoUpgrade="true">T:System.Windows.FrameworkElement</codeEntityReference>設為 [主機] 檢視的內容。</para>
          </content>
        </section>
        <section address="AddIn">
          <title>實作增益集</title>
          <content>
            <para>增益集端配接器和增益集檢視就定位之後，增益集可以實作衍生自 [增益集] 檢視中，如下列程式碼所示。</para>
            <code language="xaml">&lt;addInViews:WPFAddInView
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:addInViews="clr-namespace:AddInViews;assembly=AddInViews"
    x:Class="WPFAddIn1.AddInUI"&gt;

    &lt;Grid&gt;
        &lt;Button Click="clickMeButton_Click" Content="Click Me!" /&gt;        
    &lt;/Grid&gt;

&lt;/addInViews:WPFAddInView&gt;</code> 
            <code language="c#">using System.AddIn; // AddInAttribute
using System.Windows; // MessageBox, RoutedEventArgs

using AddInViews; // WPFAddInView

namespace WPFAddIn1
{
    /// &lt;summary&gt;
    /// Implements the add-in by deriving from WPFAddInView
    /// &lt;/summary&gt;
    [AddIn("WPF Add-In 1")]
    public partial class AddInUI : WPFAddInView
    {
        public AddInUI()
        {
            InitializeComponent();
        }

        void clickMeButton_Click(object sender, RoutedEventArgs e)
        {
            MessageBox.Show("Hello from WPFAddIn1");
        }
    }
}</code> 
          <code language="vb">Imports System.AddIn ' AddInAttribute
Imports System.Windows ' MessageBox, RoutedEventArgs

Imports AddInViews ' WPFAddInView

Namespace WPFAddIn1
    ''' &lt;summary&gt;
    ''' Implements the add-in by deriving from WPFAddInView
    ''' &lt;/summary&gt;
    &lt;AddIn("WPF Add-In 1")&gt;
    Partial Public Class AddInUI
        Inherits WPFAddInView
        Public Sub New()
            InitializeComponent()
        End Sub

        Private Sub clickMeButton_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            MessageBox.Show("Hello from WPFAddIn1")
        End Sub
    End Class
End Namespace</code>
            <para>此範例中，您可以看到有趣的好處之一，此模型︰ 增益集開發人員只需要實作增益集 (因為它是<token>TLA&#2;tla_ui</token>也)，而不是增益集類別和增益集<token>TLA&#2;tla_ui</token>。</para>
          </content>
        </section>
        <section address="HostApp">
          <title>執行主應用程式</title>
          <content>
            <para>主機端配接器和主應用程式檢視建立之後，主應用程式可以使用<token>dnprdnshort</token>增益集模型開啟管線，並取得增益集的主應用程式檢視。這些步驟是以下列程式碼所示。</para> 
            <code language="c#">// Get add-in pipeline folder (the folder in which this application was launched from)
string appPath = Environment.CurrentDirectory;

// Rebuild visual add-in pipeline
string[] warnings = AddInStore.Rebuild(appPath);
if (warnings.Length &gt; 0)
{
    string msg = "Could not rebuild pipeline:";
    foreach (string warning in warnings) msg += "\n" + warning;
    MessageBox.Show(msg);
    return;
}

// Activate add-in with Internet zone security isolation
Collection&lt;AddInToken&gt; addInTokens = AddInStore.FindAddIns(typeof(WPFAddInHostView), appPath);
AddInToken wpfAddInToken = addInTokens[0];
this.wpfAddInHostView = wpfAddInToken.Activate&lt;WPFAddInHostView&gt;(AddInSecurityLevel.Internet);

// Display add-in UI
this.addInUIHostGrid.Children.Add(this.wpfAddInHostView);</code> 
          <code language="vb">' Get add-in pipeline folder (the folder in which this application was launched from)
Dim appPath As String = Environment.CurrentDirectory

' Rebuild visual add-in pipeline
Dim warnings() As String = AddInStore.Rebuild(appPath)
If warnings.Length &gt; 0 Then
    Dim msg As String = "Could not rebuild pipeline:"
    For Each warning As String In warnings
        msg &amp;= vbLf &amp; warning
    Next warning
    MessageBox.Show(msg)
    Return
End If

' Activate add-in with Internet zone security isolation
Dim addInTokens As Collection(Of AddInToken) = AddInStore.FindAddIns(GetType(WPFAddInHostView), appPath)
Dim wpfAddInToken As AddInToken = addInTokens(0)
Me.wpfAddInHostView = wpfAddInToken.Activate(Of WPFAddInHostView)(AddInSecurityLevel.Internet)

' Display add-in UI
Me.addInUIHostGrid.Children.Add(Me.wpfAddInHostView)</code>
            <para>主應用程式會使用一般<token>dnprdnshort</token>增益集模型的程式碼，以啟動增益集，會隱含地傳回主應用程式的主應用程式檢視。主應用程式接著會顯示 [主機] 檢視 (也就是<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.UserControl</codeEntityReference>) 從<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.Grid</codeEntityReference>。</para>
            <para>處理增益集互動的程式碼<token>TLA&#2;tla_ui</token>增益集應用程式定義域中執行。這些互動包括下列︰</para>
            <list class="bullet">
              <listItem>
                <para>處理<codeEntityReference autoUpgrade="true">T:System.Windows.Controls.Button</codeEntityReference> <codeEntityReference autoUpgrade="true">E:System.Windows.Controls.Primitives.ButtonBase.Click</codeEntityReference>事件。</para>
              </listItem> 
              <listItem>
                <para>顯示<codeEntityReference autoUpgrade="true">T:System.Windows.MessageBox</codeEntityReference>。</para>
              </listItem> 
            </list>
            <para>此活動是完全獨立於主應用程式。</para>
          </content>
        </section>
      </sections>
    </legacy>
  </codeExample>
  <relatedTopics>
\<legacyLink xlink:href="8dd45b02-7218-40f9-857d-40d7b98b850b">增益集和擴充性</legacyLink>
\<link xlink:href="00b4c776-29a8-4dba-b603-280a0cdc2ade">WPF 增益集概觀</link>
</relatedTopics>
</developerHowToDocument>
