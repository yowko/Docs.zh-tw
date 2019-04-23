---
title: HOW TO：建立需要工作階段的服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 53b6c809103a2a32d544b8317164a5fa3aa81596
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300550"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a><span data-ttu-id="0a6b2-102">HOW TO：建立需要工作階段的服務</span><span class="sxs-lookup"><span data-stu-id="0a6b2-102">How to: Create a Service That Requires Sessions</span></span>
<span data-ttu-id="0a6b2-103">工作階段會在兩個或更多的端點之間建立共用狀態，以啟用諸如回呼、多重躍點安全性之類的有用功能，並在用戶端與服務執行個體之間建立關聯。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-103">Sessions create a shared state between two or more endpoints that enables useful features such as callbacks, multi-hop security, and associations between clients and service instances.</span></span> <span data-ttu-id="0a6b2-104">如需有關在 Windows Communication Foundation (WCF) 應用程式中的工作階段的詳細資訊，請參閱[使用工作階段的](../../../../docs/framework/wcf/using-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-104">For more information about sessions in Windows Communication Foundation (WCF) applications, see [Using Sessions](../../../../docs/framework/wcf/using-sessions.md).</span></span>  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a><span data-ttu-id="0a6b2-105">指定合約需要自身繫結來支援工作階段</span><span class="sxs-lookup"><span data-stu-id="0a6b2-105">To specify that a contract require its binding to support sessions</span></span>  
  
1. <span data-ttu-id="0a6b2-106">建立其中至少包含一個作業的服務合約。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-106">Create a service contract with at least one operation.</span></span> <span data-ttu-id="0a6b2-107">如需如何建立服務合約的範例，請參閱[How to:定義服務合約](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-107">For an example of how to create a service contract, see [How to: Define a Service Contract](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="0a6b2-108">將 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性設為下列其中一項，以修改宣告合約的 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="0a6b2-108">Modify the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> that declares the contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> property to either:</span></span>  
  
    -   <span data-ttu-id="0a6b2-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> (如果必須在工作階段內執行合約的話)。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-109"><xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> if this contract must be run within a session.</span></span>  
  
    -   <span data-ttu-id="0a6b2-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> (如果可以在工作階段內執行合約的話)。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-110"><xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> if this contract can be run within a session.</span></span>  
  
    -   <span data-ttu-id="0a6b2-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> (如果不得在工作階段內執行合約的話)。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-111"><xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> if this contract must not be run within a session.</span></span>  
  
3. <span data-ttu-id="0a6b2-112">將您的服務端點設定為使用支援工作階段的繫結。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-112">Configure your service endpoint to use a binding that supports sessions.</span></span> <span data-ttu-id="0a6b2-113">下列組態範例說明可支援 WS<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>ReliableMessaging 工作階段的 `-` 用法。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-113">The following configuration example shows the use of the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>, which supports a WS`-`ReliableMessaging session.</span></span>  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]   
  
## <a name="example"></a><span data-ttu-id="0a6b2-114">範例</span><span class="sxs-lookup"><span data-stu-id="0a6b2-114">Example</span></span>  
 <span data-ttu-id="0a6b2-115">下列程式碼範例說明如何指定合約層級的工作階段需求，以及透過組態檔並使用 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 繫結程序來支援該需求。</span><span class="sxs-lookup"><span data-stu-id="0a6b2-115">The following example code shows how to specify a contract-level session requirement and use a configuration file to support that requirement with the <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> binding.</span></span>  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)] 
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]      
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]     
  
## <a name="see-also"></a><span data-ttu-id="0a6b2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a6b2-116">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
