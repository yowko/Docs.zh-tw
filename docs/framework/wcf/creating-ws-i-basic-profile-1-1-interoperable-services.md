---
title: 建立 WS-I Basic Profile 1.1 互通服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: fd7828cccb1a19a17e899525d863021d3670fbdd
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389753"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="2ba45-102">建立 WS-I Basic Profile 1.1 互通服務</span><span class="sxs-lookup"><span data-stu-id="2ba45-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="2ba45-103">要將 WCF 服務終結點設定為與 ASP.NET Web 服務用戶端互通::</span><span class="sxs-lookup"><span data-stu-id="2ba45-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="2ba45-104">使用 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 型別作為服務端點的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="2ba45-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="2ba45-105">請勿使用回呼與工作階段合約功能，或在您服務端點上的異動行為</span><span class="sxs-lookup"><span data-stu-id="2ba45-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="2ba45-106">您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="2ba45-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="2ba45-107"><xref:System.ServiceModel.BasicHttpBinding> 類別的下列功能需要 WS-I Basic Profile 1.1 以外的功能：</span><span class="sxs-lookup"><span data-stu-id="2ba45-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="2ba45-108">訊息傳輸最佳化機制 (MTOM) 的訊息加密是由 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性控制。</span><span class="sxs-lookup"><span data-stu-id="2ba45-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2ba45-109">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> 不使用 MTOM。</span><span class="sxs-lookup"><span data-stu-id="2ba45-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="2ba45-110"><xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 值所控制的訊息安全性，提供符合 WS-I Basic Security Profile 1.0 的 WS-Security 支援。</span><span class="sxs-lookup"><span data-stu-id="2ba45-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="2ba45-111">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> 不使用 WS-Security。</span><span class="sxs-lookup"><span data-stu-id="2ba45-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="2ba45-112">要使 WCF 服務的中繼資料可供 ASP.NET,請使用 Web 服務用戶端生成工具[:Web 服務描述語言工具 (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29) [、Web 服務發現工具 (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)和 Visual Studio 中的**新增 Web 引用**功能。</span><span class="sxs-lookup"><span data-stu-id="2ba45-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="2ba45-113">啟用元數據發佈。</span><span class="sxs-lookup"><span data-stu-id="2ba45-113">Enable metadata publication.</span></span> <span data-ttu-id="2ba45-114">有關詳細資訊,請參閱[發佈中繼資料終結點](publishing-metadata-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="2ba45-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ba45-115">範例</span><span class="sxs-lookup"><span data-stu-id="2ba45-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2ba45-116">描述</span><span class="sxs-lookup"><span data-stu-id="2ba45-116">Description</span></span>  
 <span data-ttu-id="2ba45-117">以下範例代碼展示如何在代碼中添加與ASP.NET Web 服務用戶端相容的 WCF 終結點,或者在配置檔中添加。</span><span class="sxs-lookup"><span data-stu-id="2ba45-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2ba45-118">程式碼</span><span class="sxs-lookup"><span data-stu-id="2ba45-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2ba45-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ba45-119">See also</span></span>

- [<span data-ttu-id="2ba45-120">與 ASP.NET Web 服務的互通性</span><span class="sxs-lookup"><span data-stu-id="2ba45-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
