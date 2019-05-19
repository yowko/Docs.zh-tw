---
title: 建立 WS-I Basic Profile 1.1 互通服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 06a59c7457c0367d421cb46e33cb67f8fa039c7d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879188"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="f859d-102">建立 WS-I Basic Profile 1.1 互通服務</span><span class="sxs-lookup"><span data-stu-id="f859d-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="f859d-103">若要設定為與 ASP.NET Web 服務用戶端互通的 WCF 服務端點：</span><span class="sxs-lookup"><span data-stu-id="f859d-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="f859d-104">使用 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 型別作為服務端點的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="f859d-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="f859d-105">請勿使用回呼與工作階段合約功能，或在您服務端點上的異動行為</span><span class="sxs-lookup"><span data-stu-id="f859d-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="f859d-106">您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="f859d-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="f859d-107"><xref:System.ServiceModel.BasicHttpBinding> 類別的下列功能需要 WS-I Basic Profile 1.1 以外的功能：</span><span class="sxs-lookup"><span data-stu-id="f859d-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="f859d-108">訊息傳輸最佳化機制 (MTOM) 的訊息加密是由 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性控制。</span><span class="sxs-lookup"><span data-stu-id="f859d-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="f859d-109">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> 不使用 MTOM。</span><span class="sxs-lookup"><span data-stu-id="f859d-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="f859d-110"><xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 值所控制的訊息安全性，提供符合 WS-I Basic Security Profile 1.0 的 WS-Security 支援。</span><span class="sxs-lookup"><span data-stu-id="f859d-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="f859d-111">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> 不使用 WS-Security。</span><span class="sxs-lookup"><span data-stu-id="f859d-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="f859d-112">若要將 WCF 服務的中繼資料提供給 ASP.NET，使用 Web 服務用戶端產生工具：[Web 服務描述語言工具 (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29)， [Web 服務探索工具 (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)，和`Add Web Reference`功能在 Visual Studio 中，您必須啟用發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f859d-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="f859d-113">如需詳細資訊，請參閱 <<c0> [ 發行中繼資料端點](../../../docs/framework/wcf/publishing-metadata-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="f859d-113">For more information, see [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f859d-114">範例</span><span class="sxs-lookup"><span data-stu-id="f859d-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f859d-115">描述</span><span class="sxs-lookup"><span data-stu-id="f859d-115">Description</span></span>  
 <span data-ttu-id="f859d-116">下列程式碼範例示範如何新增適用於 ASP.NET Web 服務用戶端程式碼中，或者，在組態檔中的 WCF 端點。</span><span class="sxs-lookup"><span data-stu-id="f859d-116">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f859d-117">程式碼</span><span class="sxs-lookup"><span data-stu-id="f859d-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f859d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f859d-118">See also</span></span>

- [<span data-ttu-id="f859d-119">與 ASP.NET Web 服務的互通性</span><span class="sxs-lookup"><span data-stu-id="f859d-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
