---
title: HOW TO：使用 Svcutil.exe 來下載中繼資料文件
description: 瞭解如何使用 Svcutil.exe 從執行中服務下載中繼資料，並將中繼資料儲存至本機檔案。
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 42df55fe7bbae6d8c977263e05053d8a8fa87aff
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246762"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="37057-103">HOW TO：使用 Svcutil.exe 來下載中繼資料文件</span><span class="sxs-lookup"><span data-stu-id="37057-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>
<span data-ttu-id="37057-104">您可以使用 Svcutil.exe 從正在執行的服務下載中繼資料，並將該中繼資料儲存至本機檔案。</span><span class="sxs-lookup"><span data-stu-id="37057-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="37057-105">針對 HTTP 和 HTTPS URL 配置，Svcutil.exe 嘗試使用透過 ws-metadataexchange 和[XML Web Service 探索](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100))來抓取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37057-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="37057-106">對於所有其他的 URL 配置，Svcutil.exe 只會使用 WS-MetadataExchange。</span><span class="sxs-lookup"><span data-stu-id="37057-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="37057-107">根據預設，Svcutil.exe 會使用定義於 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 類別的繫結。</span><span class="sxs-lookup"><span data-stu-id="37057-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="37057-108">若要設定用於 WS-MetadataExchange 的繫結，您必須在 Svcutil.exe 的組態檔 (svcutil.exe.config) 中定義用戶端端點，該端點會使用 `IMetadataExchange` 合約，而且使用名稱就是中繼資料端點位址的統一資源識別元 (URI) 配置。</span><span class="sxs-lookup"><span data-stu-id="37057-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="37057-109">當您執行 Svcutil.exe 來取得服務的中繼資料，而這兩個服務合約分別包含相同名稱的作業時，Svcutil.exe 會顯示錯誤，指出「無法取得來自 ... 的中繼資料」。例如，如果您的服務會公開名為且具有作業的服務合約， `ICarService` `Get(Car c)` 而且相同的服務會公開名為且具有作業的服務合約 `IBookService` `Get(Book b)` 。</span><span class="sxs-lookup"><span data-stu-id="37057-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="37057-110">若要解決這個問題，請執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="37057-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="37057-111">重新命名其中一項作業。</span><span class="sxs-lookup"><span data-stu-id="37057-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="37057-112">將 <xref:System.ServiceModel.OperationContractAttribute.Name%2A> 設定為另一個名稱。</span><span class="sxs-lookup"><span data-stu-id="37057-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="37057-113">使用 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性，將其中一項作業的命名空間設定為另一個命名空間。</span><span class="sxs-lookup"><span data-stu-id="37057-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="37057-114">使用 Svcutil.exe 來下載中繼資料</span><span class="sxs-lookup"><span data-stu-id="37057-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="37057-115">在下列位置找到 Svcutil.exe 工具：</span><span class="sxs-lookup"><span data-stu-id="37057-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="37057-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="37057-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="37057-117">在命令提示字元中，使用下列格式啟動該工具。</span><span class="sxs-lookup"><span data-stu-id="37057-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="37057-118">您必須指定 `/t:metadata` 選項才能下載中繼資料。</span><span class="sxs-lookup"><span data-stu-id="37057-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="37057-119">否則，便會產生用戶端程式碼與組態。</span><span class="sxs-lookup"><span data-stu-id="37057-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="37057-120"><`url`>引數會指定提供中繼資料之服務端點的 URL，或是線上裝載之元資料檔案的 URL。</span><span class="sxs-lookup"><span data-stu-id="37057-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="37057-121"><`epr`> 引數會指定 XML 檔案的路徑，該檔案包含 `EndpointAddress` 支援透過 ws-metadataexchange 之服務端點的 ws-addressing。</span><span class="sxs-lookup"><span data-stu-id="37057-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="37057-122">如需有關使用此工具來下載中繼資料的更多選項，請參閱[System.servicemodel 中繼資料公用程式工具（Svcutil.exe）](../servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="37057-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37057-123">範例</span><span class="sxs-lookup"><span data-stu-id="37057-123">Example</span></span>  
 <span data-ttu-id="37057-124">下列命令會從正在執行的服務下載中繼資料文件。</span><span class="sxs-lookup"><span data-stu-id="37057-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="37057-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37057-125">See also</span></span>

- [<span data-ttu-id="37057-126">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="37057-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
