---
title: ".NET Framework 4.6 中的重定目標變更 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retargeting changes, .NET Framework
- retargeting changes, .NET Framework 4.6
- application compatibility
ms.assetid: fa849255-f90f-4bf1-b0ff-b173c12110d7
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 19ad80233a79a4fdef89550696c1c3d33e14b355
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="retargeting-changes-in-the-net-framework-46"></a>.NET Framework 4.6 中的重定目標變更
在某些罕見的情況下，重定目標變更可能會影響以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為目標來重新編譯的應用程式。 除非另有指定，否則這些變更不會影響以舊版 .NET Framework 為目標但在[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]下執行的二進位檔。  
  
 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 包含下列區域的重定目標變更：  
  
-   [核心](#Core)  
  
-   [ASP.NET](#ASP)  
  
-   [網路](#Net)  
  
-   [Windows Communications Foundation (WCF)](#WCF)  
  
-   [Windows Forms](#WinForms)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
-   [XML](#XML)  
  
<a name="Core"></a>   
## <a name="core"></a>核心  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>，以及具有 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 之以工作為基礎的非同步作業|對於以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 和更新版本為目標的應用程式，<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 是儲存在執行緒的 <xref:System.Threading.ExecutionContext> 中，而它會在非同步作業之間流動。|對於 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性的變更會反映在後續啟動的非同步作業中。 如需詳細資訊，請參閱[風險降低：文化特性和非同步作業](../../../docs/framework/migration-guide/mitigation-culture-and-asynchronous-operations.md)。|次要|  
  
<a name="ASP"></a>   
## <a name="aspnet"></a>ASP.NET  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|具有值為 <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> 之 `tagKey` 的 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName>|為了符合 HTML 標準，<xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> 方法現在會在 HTML 回應中將 <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> 轉譯為非結尾標記。|BR 標記現在會產生一個分行符號。 先前會產生兩個分行符號。<br /><br /> 依賴 `<BR>` 標記來產生兩個分行符號的應用程式可還原先前的行為，方法是使用 <xref:System.Web.UI.HtmlTextWriterTag?displayProperty=fullName> 引數對 <xref:System.Web.UI.HtmlTextWriter.RenderBeginTag%28System.Web.UI.HtmlTextWriterTag%29?displayProperty=fullName> 方法進行額外的呼叫。|次要|  
  
<a name="Net"></a>   
## <a name="networking"></a>網路  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Net.ServicePointManager?displayProperty=fullName> 和 <xref:System.Net.Security.SslStream?displayProperty=fullName>|從目標為 .NET Framework 4.6 的應用程式開始，<xref:System.Net.ServicePointManager?displayProperty=fullName> 和 <xref:System.Net.Security.SslStream?displayProperty=fullName> 類別可以使用 Tls1.0、Tls1.1 或 Tls 1.2 這三種通訊協定之一。<br /><br /> 若是目標為舊版 .NET Framework 的應用程式，即使在 NET Framework 4.6 上執行也不會受到影響。|這項變更會影響任何使用 SSL 與 HTTPS 伺服器通訊或與使用任何下列類型之通訊端伺服器通訊，且目標為 .NET Framework 4.6 的應用程式：<xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient> 和 <xref:System.Net.Security.SslStream>。  如需詳細資訊，請參閱[風險降低：TLS 通訊協定](../../../docs/framework/migration-guide/mitigation-tls-protocols.md)。|次要|  
  
<a name="WCF"></a>   
## <a name="windows-communications-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|特殊功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%2A?displayProperty=fullName>|使用 `null``authorizationPolicies` 引數呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext%28System.Collections.Generic.IList%7BSystem.IdentityModel.Policy.IAuthorizationPolicy%7D%29> 所傳回的 <xref:System.IdentityModel.Policy.AuthorizationContext> 實作，已變更其在 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 中的實作。|在少數情況下，使用自訂驗證的 WCF 應用程式，在行為上可能會有些許差異。 如需舊版行為，請參閱[風險降低：預設的 AuthorizationContext](../../../docs/framework/migration-guide/mitigation-default-authorizationcontext.md)。|次要|  
  
<a name="WinForms"></a>   
## <a name="windows-forms"></a>Windows Form  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName>|從以 .NET Framework 4.6 為目標的應用程式開始，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> 方法可將具有 PNG 畫面格的圖示成功轉換成 <xref:System.Drawing.Bitmap> 物件。<br /><br /> 在以 .NET Framework 4.5.2 和更早版本為目標的應用程式中，如果 <xref:System.Drawing.Icon> 物件具有 PNG 畫面格，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> 方法會擲回 <xref:System.ArgumentOutOfRangeException> 例外狀況。|這項變更會影響重新編譯為以 .NET Framework 4.6 為目標的應用程式，以及針對 <xref:System.Drawing.Icon> 物件具有 PNG 畫面格時所擲回的 <xref:System.ArgumentOutOfRangeException> 例外狀況提供特殊處理的應用程式。 如果不需要這種行為，設定參數可還原先前的行為。 如需詳細資訊，請參閱[風險降低：Icon 物件中的 PNG 畫面格](../../../docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md)。|次要|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>|在以 .NET Framework 4.6 和 .NET Framework 4.6.1 為目標的應用程式中，在 <xref:System.Windows.Threading.Dispatcher> 中對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性進行的變更，會於發送器作業結束時遺失。 同樣地，在發送器作業之外對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 所做的變更，可能不會在執行該作業時反映出來。|對 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 屬性的變更可能不會在 WPF UI 回呼和 WPF 應用程式中其他程式碼之間流動。 如需詳細資訊，請參閱[風險降低：WPF 應用程式中的文化特性和發送器作業](../../../docs/framework/migration-guide/mitigation-culture-and-dispatcher-operations-in-wpf-apps.md)。|次要|  
|高 DPI 的版面配置進位|邊界的進位方式以及邊界內部的框線和背景皆有所變更。|WPF 控制項的版面配置可能略有不同。 如需詳細資訊，請參閱[風險降低：WPF 版面配置](../../../docs/framework/migration-guide/mitigation-wpf-layout.md)。|次要|  
  
<a name="XML"></a>   
## <a name="xml"></a>XML  
  
|功能|變更|影響|範圍|  
|-------------|------------|------------|-----------|  
|XSD 結構描述驗證|從 .NET Framework 4.6 開始，如果使用複合索引鍵且其中一個索引鍵是空的，則 XSD 結構描述驗證會偵測出唯一條件約束違規。|[風險降低：XML 結構描述驗證](../../../docs/framework/migration-guide/mitigation-xml-schema-validation.md)|次要|  
|<xref:System.Xml.XmlWriter>|針對以 .NET Framework 4.5.2 或之前版本為目標的應用程式，使用例外狀況後援處理寫入無效的 Surrogate 字組時不一定每次都會擲回例外狀況。<br /><br /> 針對以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為目標的應用程式，嘗試寫入無效的 Surrogate 字組會擲回 <xref:System.ArgumentException> 例外狀況。|重新編譯成以 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 為目標以及寫入無效 Surrogate 字組的應用程式會在先前沒有的情況下擲回例外狀況。|邊緣|
