---
title: 建立 WS-I Basic Profile 1.1 互通服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: eb1cd12c45a276d5c3cb14f89205fff618121abc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320134"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="882ce-102">建立 WS-I Basic Profile 1.1 互通服務</span><span class="sxs-lookup"><span data-stu-id="882ce-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="882ce-103">若要將 WCF 服務端點設定為可與 ASP.NET Web 服務用戶端互通：</span><span class="sxs-lookup"><span data-stu-id="882ce-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="882ce-104">使用 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 型別作為服務端點的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="882ce-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="882ce-105">請勿使用回呼與工作階段合約功能，或在您服務端點上的異動行為</span><span class="sxs-lookup"><span data-stu-id="882ce-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="882ce-106">您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="882ce-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="882ce-107"><xref:System.ServiceModel.BasicHttpBinding> 類別的下列功能需要 WS-I Basic Profile 1.1 以外的功能：</span><span class="sxs-lookup"><span data-stu-id="882ce-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="882ce-108">訊息傳輸最佳化機制 (MTOM) 的訊息加密是由 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性控制。</span><span class="sxs-lookup"><span data-stu-id="882ce-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="882ce-109">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> 不使用 MTOM。</span><span class="sxs-lookup"><span data-stu-id="882ce-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="882ce-110"><xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 值所控制的訊息安全性，提供符合 WS-I Basic Security Profile 1.0 的 WS-Security 支援。</span><span class="sxs-lookup"><span data-stu-id="882ce-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="882ce-111">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> 不使用 WS-Security。</span><span class="sxs-lookup"><span data-stu-id="882ce-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="882ce-112">若要讓 WCF 服務的中繼資料可供 ASP.NET，請使用 Web 服務用戶端產生工具： [web 服務描述語言工具（wsdl.exe）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29)、 [Web 服務探索工具（Disco）](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)和 Visual Studio 中的 `Add Web Reference` 功能;您必須啟用中繼資料發行。</span><span class="sxs-lookup"><span data-stu-id="882ce-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29), [Web Services Discovery Tool (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29), and the `Add Web Reference` feature in Visual Studio; you must enable metadata publication.</span></span> <span data-ttu-id="882ce-113">如需詳細資訊，請參閱[發行中繼資料端點](publishing-metadata-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="882ce-113">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="882ce-114">範例</span><span class="sxs-lookup"><span data-stu-id="882ce-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="882ce-115">描述</span><span class="sxs-lookup"><span data-stu-id="882ce-115">Description</span></span>  
 <span data-ttu-id="882ce-116">下列範例程式碼示範如何在程式碼中新增與 ASP.NET Web 服務用戶端相容的 WCF 端點，或者在設定檔中加入。</span><span class="sxs-lookup"><span data-stu-id="882ce-116">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="882ce-117">程式碼</span><span class="sxs-lookup"><span data-stu-id="882ce-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="882ce-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="882ce-118">See also</span></span>

- [<span data-ttu-id="882ce-119">與 ASP.NET Web 服務的互通性</span><span class="sxs-lookup"><span data-stu-id="882ce-119">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
