---
title: "建立 WS-I Basic Profile 1.1 互通服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6bef68c8ba433e902cfd50e59a3b343e3af08cd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="01be2-102">建立 WS-I Basic Profile 1.1 互通服務</span><span class="sxs-lookup"><span data-stu-id="01be2-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="01be2-103">將 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務端點設成與 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web 服務用戶端互通：</span><span class="sxs-lookup"><span data-stu-id="01be2-103">To configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service endpoint to be interoperable with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients:</span></span>  
  
-   <span data-ttu-id="01be2-104">使用 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 型別作為服務端點的繫結型別。</span><span class="sxs-lookup"><span data-stu-id="01be2-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
-   <span data-ttu-id="01be2-105">請勿使用回呼與工作階段合約功能，或在您服務端點上的交易行為</span><span class="sxs-lookup"><span data-stu-id="01be2-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
 <span data-ttu-id="01be2-106">您可選擇啟用 HTTPS 支援及對繫結的傳輸層級用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="01be2-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
 <span data-ttu-id="01be2-107"><xref:System.ServiceModel.BasicHttpBinding> 類別的下列功能需要 WS-I Basic Profile 1.1 以外的功能：</span><span class="sxs-lookup"><span data-stu-id="01be2-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
-   <span data-ttu-id="01be2-108">訊息傳輸最佳化機制 (MTOM) 的訊息加密是由 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 屬性控制。</span><span class="sxs-lookup"><span data-stu-id="01be2-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="01be2-109">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> 不使用 MTOM。</span><span class="sxs-lookup"><span data-stu-id="01be2-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
-   <span data-ttu-id="01be2-110"><xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 值所控制的訊息安全性，提供符合 WS-I Basic Security Profile 1.0 的 WS-Security 支援。</span><span class="sxs-lookup"><span data-stu-id="01be2-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="01be2-111">將此屬性保留為預設值，也就是 <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> 不使用 WS-Security。</span><span class="sxs-lookup"><span data-stu-id="01be2-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
 <span data-ttu-id="01be2-112">若要將中繼資料給[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]可用來服務[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]，使用 Web 服務用戶端產生工具： [Web 服務描述語言工具 (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88)， [Web 服務探索工具 (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979)，而`Add Web Reference`功能[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; 您必須啟用發行中繼資料。</span><span class="sxs-lookup"><span data-stu-id="01be2-112">To make the metadata for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service available to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](http://msdn.microsoft.com/library/b9210348-8bc2-4367-8c91-d1a04b403e88), [Web Services Discovery Tool (Disco.exe)](http://msdn.microsoft.com/library/acd88078-c581-42bc-94ca-6633e2851979), and the `Add Web Reference` feature in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]; you must enable metadata publication.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="01be2-113">[發行中繼資料端點](../../../docs/framework/wcf/publishing-metadata-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="01be2-113"> [Publishing Metadata Endpoints](../../../docs/framework/wcf/publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01be2-114">範例</span><span class="sxs-lookup"><span data-stu-id="01be2-114">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="01be2-115">描述</span><span class="sxs-lookup"><span data-stu-id="01be2-115">Description</span></span>  
 <span data-ttu-id="01be2-116">下列程式碼範例示範如何將[!INCLUDE[indigo2](../../../includes/indigo2-md.md)]與相容的端點[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]Web 服務用戶端程式碼中的，或者，在組態檔中。</span><span class="sxs-lookup"><span data-stu-id="01be2-116">The following example code demonstrates how to add a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] endpoint that is compatible with [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="01be2-117">程式碼</span><span class="sxs-lookup"><span data-stu-id="01be2-117">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01be2-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="01be2-118">See Also</span></span>  
 [<span data-ttu-id="01be2-119">與 ASP.NET Web 服務的互通性</span><span class="sxs-lookup"><span data-stu-id="01be2-119">Interoperability with ASP.NET Web Services</span></span>](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
