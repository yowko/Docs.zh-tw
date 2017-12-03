---
title: "HOW TO：使用 Svcutil.exe 來下載中繼資料文件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6868bbecd83305c07e0b547d0102d7bca48d41f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="c829d-102">HOW TO：使用 Svcutil.exe 來下載中繼資料文件</span><span class="sxs-lookup"><span data-stu-id="c829d-102">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="c829d-103">您可以使用 Svcutil.exe 從正在執行的服務下載中繼資料，並將該中繼資料儲存至本機檔案。</span><span class="sxs-lookup"><span data-stu-id="c829d-103">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="c829d-104">對於 HTTP 和 HTTPS URL 結構描述，Svcutil.exe 會嘗試使用 Ws-metadataexchange 擷取中繼資料和[XML Web 服務探索](http://go.microsoft.com/fwlink/?LinkId=94950)。</span><span class="sxs-lookup"><span data-stu-id="c829d-104">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](http://go.microsoft.com/fwlink/?LinkId=94950).</span></span> <span data-ttu-id="c829d-105">對於所有其他的 URL 配置，Svcutil.exe 只會使用 WS-MetadataExchange。</span><span class="sxs-lookup"><span data-stu-id="c829d-105">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="c829d-106">根據預設，Svcutil.exe 會使用定義於 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 類別的繫結。</span><span class="sxs-lookup"><span data-stu-id="c829d-106">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="c829d-107">若要設定用於 WS-MetadataExchange 的繫結，您必須在 Svcutil.exe 的組態檔 (svcutil.exe.config) 中定義用戶端端點，該端點會使用 `IMetadataExchange` 合約，而且使用名稱就是中繼資料端點位址的統一資源識別元 (URI) 配置。</span><span class="sxs-lookup"><span data-stu-id="c829d-107">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c829d-108">當執行 Svcutil.exe 取得中繼資料之服務公開兩個不同的服務合約，每個包含相同名稱的作業時，Svcutil.exe 就會顯示 「 無法取得中繼資料從...」 的錯誤訊息，比方說，如果您有公開稱為 「 服務合約的服務作業的某 Get (Car c) 和相同的服務會公開名為 IBookService 具有 Get (Book b) 作業的服務合約。</span><span class="sxs-lookup"><span data-stu-id="c829d-108">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called ICarService that has an operation Get(Car c) and the same service exposes a service contract called IBookService that has an operation Get(Book b).</span></span> <span data-ttu-id="c829d-109">為了解決此問題，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c829d-109">To work around this issue, do one of the following:</span></span>  
>   
>  -   <span data-ttu-id="c829d-110">重新命名其中一項作業</span><span class="sxs-lookup"><span data-stu-id="c829d-110">Rename one of the operations</span></span>  
> -   <span data-ttu-id="c829d-111">將 <xref:System.ServiceModel.OperationContractAttribute.Name%2A> 設定為另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="c829d-111">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>  
> -   <span data-ttu-id="c829d-112">使用 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性，將其中一項作業的命名空間設定為另一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="c829d-112">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
### <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="c829d-113">使用 Svcutil.exe 來下載中繼資料</span><span class="sxs-lookup"><span data-stu-id="c829d-113">To download metadata using Svcutil.exe</span></span>  
  
1.  <span data-ttu-id="c829d-114">在下列位置找到 Svcutil.exe 工具：</span><span class="sxs-lookup"><span data-stu-id="c829d-114">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="c829d-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="c829d-115">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2.  <span data-ttu-id="c829d-116">在命令提示字元中，使用下列格式啟動該工具。</span><span class="sxs-lookup"><span data-stu-id="c829d-116">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="c829d-117">您必須指定 `/t:metadata` 選項才能下載中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c829d-117">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="c829d-118">否則，便會產生用戶端程式碼與組態。</span><span class="sxs-lookup"><span data-stu-id="c829d-118">Otherwise, client code and configuration are generated.</span></span>  
  
3.  <span data-ttu-id="c829d-119"><`url`> 引數會指定提供中繼資料之服務端點或裝載於線上之中繼資料文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="c829d-119">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="c829d-120"><`epr`> 引數會指定包含 WS 定址為 XML 檔案的路徑`EndpointAddress`支援 Ws-metadataexchange 之服務端點。</span><span class="sxs-lookup"><span data-stu-id="c829d-120">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="c829d-121">如需使用中繼資料下載此工具的更多選項，請參閱[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="c829d-121">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c829d-122">範例</span><span class="sxs-lookup"><span data-stu-id="c829d-122">Example</span></span>  
 <span data-ttu-id="c829d-123">下列命令會從正在執行的服務下載中繼資料文件。</span><span class="sxs-lookup"><span data-stu-id="c829d-123">The following command downloads metadata documents from a running service.</span></span>  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="c829d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c829d-124">See Also</span></span>  
 [<span data-ttu-id="c829d-125">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c829d-125">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
