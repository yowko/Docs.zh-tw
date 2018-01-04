---
title: "中繼資料擴充性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f92fcc76-0806-4c84-9d63-7aae0d3899de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb1ee59e2feca3344aabc4be81ae1d5637b3d545
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-extensibility"></a><span data-ttu-id="918c8-102">中繼資料擴充性</span><span class="sxs-lookup"><span data-stu-id="918c8-102">Metadata Extensibility</span></span>
<span data-ttu-id="918c8-103">本節包含示範自訂中繼資料的範例。</span><span class="sxs-lookup"><span data-stu-id="918c8-103">This section contains samples that demonstrate custom metadata.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="918c8-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="918c8-104">In This Section</span></span>  
 [<span data-ttu-id="918c8-105">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="918c8-105">Custom Secure Metadata Endpoint</span></span>](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 <span data-ttu-id="918c8-106">示範如何實作使用安全的中繼資料端點，使用其中一個是非中繼資料交換繫結的服務，以及如何設定[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)或擷取的中繼資料的用戶端這類中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="918c8-106">Demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span>  
  
 [<span data-ttu-id="918c8-107">自訂 WSDL 發行集</span><span class="sxs-lookup"><span data-stu-id="918c8-107">Custom WSDL Publication</span></span>](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 <span data-ttu-id="918c8-108">除了其他功能之外，還會示範如何在自訂 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 屬性 (Attribute) 上實作 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>，以便將屬性 (Attribute) 的屬性 (Property) 匯出為 WSDL 附註。</span><span class="sxs-lookup"><span data-stu-id="918c8-108">Demonstrates how to implement a <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> on a custom <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> attribute to export attribute properties as WSDL annotations, among other functionality.</span></span>
