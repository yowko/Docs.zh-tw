---
title: "HOW TO：擷取中繼資料並實作相容性服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33090cd855aa41607f6d330d695f24a6f60197d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a><span data-ttu-id="be16d-102">HOW TO：擷取中繼資料並實作相容性服務</span><span class="sxs-lookup"><span data-stu-id="be16d-102">How to: Retrieve Metadata and Implement a Compliant Service</span></span>
<span data-ttu-id="be16d-103">服務通常不會由同一個人設計並實作。</span><span class="sxs-lookup"><span data-stu-id="be16d-103">Often, the same person does not design and implement services.</span></span> <span data-ttu-id="be16d-104">在重視應用程式之間互通性的環境中，可以使用 Web 服務描述語言 (WSDL) 來設計或描述合約，而開發人員則必須實作符合所提供合約的服務。</span><span class="sxs-lookup"><span data-stu-id="be16d-104">In environments where interoperating applications are important, contracts can be designed or described in Web Services Description Language (WSDL) and a developer must implement a service that complies with the provided contract.</span></span> <span data-ttu-id="be16d-105">您也可能想要將現有服務移轉至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]，但是保留 Wire 格式。</span><span class="sxs-lookup"><span data-stu-id="be16d-105">You may also want to migrate an existing service to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] but preserve the wire format.</span></span> <span data-ttu-id="be16d-106">此外，雙工合約還會要求呼叫端也必須實作回呼合約。</span><span class="sxs-lookup"><span data-stu-id="be16d-106">In addition, duplex contracts require callers to implement a callback contract as well.</span></span>  
  
 <span data-ttu-id="be16d-107">在這些情況下，您必須使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) （或對等的工具） 來產生服務合約介面的受管理的語言，您可以實作以滿足的需求合約。</span><span class="sxs-lookup"><span data-stu-id="be16d-107">In these cases, you must use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (or an equivalent tool) to generate a service contract interface in a managed language that you can implement to fulfill the requirements of the contract.</span></span> <span data-ttu-id="be16d-108">通常[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)用來取得通道處理站搭配使用的服務合約或[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端類型以及設定用戶端組態檔正確的繫結和位址。</span><span class="sxs-lookup"><span data-stu-id="be16d-108">Typically the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is used to acquire a service contract that is used with a channel factory or a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client type as well as with a client configuration file that sets up the correct binding and address.</span></span> <span data-ttu-id="be16d-109">若要使用產生的組態檔，您必須將它變更為服務組態檔。</span><span class="sxs-lookup"><span data-stu-id="be16d-109">To use the generated configuration file, you must change it into a service configuration file.</span></span> <span data-ttu-id="be16d-110">您可能還需要修改服務合約。</span><span class="sxs-lookup"><span data-stu-id="be16d-110">You may also need to modify the service contract.</span></span>  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a><span data-ttu-id="be16d-111">若要擷取資料並實作相容服務</span><span class="sxs-lookup"><span data-stu-id="be16d-111">To retrieve data and implement a compliant service</span></span>  
  
1.  <span data-ttu-id="be16d-112">使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)對中繼資料檔案或產生的程式碼檔案中繼資料端點。</span><span class="sxs-lookup"><span data-stu-id="be16d-112">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) against metadata files or a metadata endpoint to generate a code file.</span></span>  
  
2.  <span data-ttu-id="be16d-113">搜尋輸出程式碼檔案中包含標示有 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性之所需介面 (如果有一個以上) 的部分。</span><span class="sxs-lookup"><span data-stu-id="be16d-113">Search for the portion of the output code file that contains the interface of interest (in case there is more than one) that is marked with the <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="be16d-114">下列程式碼範例顯示所產生的兩個介面[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="be16d-114">The following code example shows the two interfaces generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="be16d-115">第一個 (`ISampleService`) 是您為了建立相容服務而實作的服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="be16d-115">The first (`ISampleService`) is the service contract interface that you implement to create a compliant service.</span></span> <span data-ttu-id="be16d-116">第二個 (`ISampleServiceChannel`) 是供用戶端使用的 Helper 介面，這個介面會擴充服務合約介面及 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>，而且可以在用戶端應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="be16d-116">The second (`ISampleServiceChannel`) is a helper interface for client use that extends both the service contract interface and <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> and is for use in a client application.</span></span>  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  <span data-ttu-id="be16d-117">如果 WSDL 沒有為所有的作業指定回覆動作，則產生的作業合約可能會將 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 屬性設定為萬用字元 (*)。</span><span class="sxs-lookup"><span data-stu-id="be16d-117">If the WSDL does not specify a reply action for all of the operations, the generated operation contracts may have the <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> property set to the wildcard character (*).</span></span> <span data-ttu-id="be16d-118">請移除這個屬性設定。</span><span class="sxs-lookup"><span data-stu-id="be16d-118">Remove this property setting.</span></span> <span data-ttu-id="be16d-119">否則，當您實作服務合約中繼資料時，就無法匯出這些作業的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="be16d-119">Otherwise, when you implement the service contract metadata, the metadata cannot be exported for those operations.</span></span>  
  
4.  <span data-ttu-id="be16d-120">在類別上實作介面並裝載服務。</span><span class="sxs-lookup"><span data-stu-id="be16d-120">Implement the interface on a class and host the service.</span></span> <span data-ttu-id="be16d-121">如需範例，請參閱[How to： 實作服務合約](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)，或請參閱下方範例 > 一節中的簡單實作。</span><span class="sxs-lookup"><span data-stu-id="be16d-121">For an example, see [How to: Implement a Service Contract](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), or see a simple implementation below in the Example section.</span></span>  
  
5.  <span data-ttu-id="be16d-122">在用戶端組態檔中的[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)產生時，變更[\<用戶端 >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)的組態區段[ \<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段。</span><span class="sxs-lookup"><span data-stu-id="be16d-122">In the client configuration file that the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generates, change the [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) configuration section to a [\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuration section.</span></span> <span data-ttu-id="be16d-123">(如需所產生之用戶端應用程式組態檔的範例，請參閱下列＜範例＞一節)。</span><span class="sxs-lookup"><span data-stu-id="be16d-123">(For an example of a generated client application configuration file, see the following "Example" section.)</span></span>  
  
6.  <span data-ttu-id="be16d-124">內[\<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段中，建立`name`屬性[\<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)組態區段，為您的服務實作。</span><span class="sxs-lookup"><span data-stu-id="be16d-124">Within the [\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuration section, create a `name` attribute in the [\<services>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuration section for your service implementation.</span></span>  
  
7.  <span data-ttu-id="be16d-125">將服務的 `name` 屬性設定為服務實作的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="be16d-125">Set the service `name` attribute to the configuration name for your service implementation.</span></span>  
  
8.  <span data-ttu-id="be16d-126">將使用實作服務合約的端點組態項目加入至服務組態區段。</span><span class="sxs-lookup"><span data-stu-id="be16d-126">Add the endpoint configuration elements that use the implemented service contract to the service configuration section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be16d-127">範例</span><span class="sxs-lookup"><span data-stu-id="be16d-127">Example</span></span>  
 <span data-ttu-id="be16d-128">下列程式碼範例示範執行所產生的程式碼檔案的大部分[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)針對中繼資料檔案。</span><span class="sxs-lookup"><span data-stu-id="be16d-128">The following code example shows the majority of a code file generated by running the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) against metadata files.</span></span>  
  
 <span data-ttu-id="be16d-129">下列程式碼顯示：</span><span class="sxs-lookup"><span data-stu-id="be16d-129">The following code shows:</span></span>  
  
-   <span data-ttu-id="be16d-130">服務合約介面，這個介面會在實作之後符合合約需求 (`ISampleService`)。</span><span class="sxs-lookup"><span data-stu-id="be16d-130">The service contract interface that, when implemented, complies with the contract requirements (`ISampleService`).</span></span>  
  
-   <span data-ttu-id="be16d-131">供用戶端使用的 Helper 介面，這個介面會擴充服務合約介面及 <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>，而且可以在用戶端應用程式中 (`ISampleServiceChannel`) 使用。</span><span class="sxs-lookup"><span data-stu-id="be16d-131">The helper interface for client use that extends both the service contract interface and <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> and is for use in a client application (`ISampleServiceChannel`).</span></span>  
  
-   <span data-ttu-id="be16d-132">Helper 類別，這個類別會擴充 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>，而且可以在用戶端應用程式 (`SampleServiceClient`) 中使用。</span><span class="sxs-lookup"><span data-stu-id="be16d-132">The helper class that extends <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> and is for use in a client application (`SampleServiceClient`).</span></span>  
  
-   <span data-ttu-id="be16d-133">從服務產生的組態檔。</span><span class="sxs-lookup"><span data-stu-id="be16d-133">The configuration file generated from the service.</span></span>  
  
-   <span data-ttu-id="be16d-134">簡易 `ISampleService` 服務實作。</span><span class="sxs-lookup"><span data-stu-id="be16d-134">A simple `ISampleService` service implementation.</span></span>  
  
-   <span data-ttu-id="be16d-135">用戶端組態檔轉換為服務端版。</span><span class="sxs-lookup"><span data-stu-id="be16d-135">A conversion of the client-side configuration file to a service-side version.</span></span>  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]    
 [!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    
 [!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a><span data-ttu-id="be16d-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be16d-136">See Also</span></span>  
 [<span data-ttu-id="be16d-137">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="be16d-137">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
