---
title: "整合 COM 應用程式概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b20ae5329f08e9391fd7b93218c44c3c1978a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="09172-102">整合 COM 應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="09172-102">Integrating with COM Applications Overview</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="09172-103"> 為 Managed 程式碼開發人員提供了一個資源豐富的作業環境，讓他們可以建立相關應用程式。</span><span class="sxs-lookup"><span data-stu-id="09172-103"> provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="09172-104">不過，如果您對 Unmanaged COM 架構程式碼做了大筆投資，而且不想進行移轉，則仍舊可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker 將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務直接移轉至現有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="09172-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="09172-105">服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。</span><span class="sxs-lookup"><span data-stu-id="09172-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09172-106">服務 Moniker 會在所有的通訊中使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通訊通道。</span><span class="sxs-lookup"><span data-stu-id="09172-106">The service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel for all communication.</span></span> <span data-ttu-id="09172-107">該通道的安全性和識別機制不同於標準 COM 和 DCOM Proxy 所使用的機制。</span><span class="sxs-lookup"><span data-stu-id="09172-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="09172-108">此外，服務 Moniker 會使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通訊通道，所以任何呼叫的預設逾時期間都是一分鐘。</span><span class="sxs-lookup"><span data-stu-id="09172-108">In addition, because the service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="09172-109">服務 Moniker 會搭配 `GetObject` 函式使用，提供 Unmanaged 開發人員強型別且專屬於 COM 的方法來呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務。</span><span class="sxs-lookup"><span data-stu-id="09172-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services.</span></span> <span data-ttu-id="09172-110">這個動作需要有 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務合約的本機 COM 可見定義，以及要使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="09172-110">This requires a local, COM-visible definition of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="09172-111">正如其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端一樣，雖然在第一次呼叫方法時，COM 程式設計人員看得見這個通道建構過程，但服務 Moniker 仍必須建構服務的型別通道。</span><span class="sxs-lookup"><span data-stu-id="09172-111">Like other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="09172-112">與其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端共通的是，當使用 Moniker 時，應用程式會將位址、繫結及合約指定為與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="09172-112">In common with other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="09172-113">可以使用下列其中一種方法指定合約：</span><span class="sxs-lookup"><span data-stu-id="09172-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="09172-114">型別合約：合約會在用戶端電腦上註冊為 COM 可見型別。</span><span class="sxs-lookup"><span data-stu-id="09172-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="09172-115">WSDL 合約：合約會以 WSDL 文件的形式提供。</span><span class="sxs-lookup"><span data-stu-id="09172-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="09172-116">MEX 合約：合約會在執行階段從中繼資料交換 (MEX) 端點擷取。</span><span class="sxs-lookup"><span data-stu-id="09172-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="09172-117">服務 Moniker 支援的參數</span><span class="sxs-lookup"><span data-stu-id="09172-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="09172-118">下表顯示服務 Moniker 所支援的參數。</span><span class="sxs-lookup"><span data-stu-id="09172-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="09172-119">參數</span><span class="sxs-lookup"><span data-stu-id="09172-119">Parameter</span></span>|<span data-ttu-id="09172-120">描述</span><span class="sxs-lookup"><span data-stu-id="09172-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="09172-121">服務的 URL 位置。</span><span class="sxs-lookup"><span data-stu-id="09172-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="09172-122">應用程式組態中的繫結區段名稱。</span><span class="sxs-lookup"><span data-stu-id="09172-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="09172-123">具名繫結區段中的具名繫結執行個體。</span><span class="sxs-lookup"><span data-stu-id="09172-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="09172-124">介面識別項 (IID)，表示服務合約或合約名稱 (來自 MEX)。</span><span class="sxs-lookup"><span data-stu-id="09172-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="09172-125">WSDL 文件，提供其他形式的合約定義。</span><span class="sxs-lookup"><span data-stu-id="09172-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="09172-126">伺服器主要名稱 (SPN) 身分識別，用於與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="09172-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="09172-127">使用者主要名稱 (UPN) 身分識別，用於與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="09172-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="09172-128">DNS 身分識別，用於與服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="09172-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="09172-129">服務中繼資料交換 (MEX) 端點的 URL 位置。</span><span class="sxs-lookup"><span data-stu-id="09172-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="09172-130">要連接 MEX 端點之應用程式組態中的繫結區段名稱。</span><span class="sxs-lookup"><span data-stu-id="09172-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="09172-131">要連接 MEX 端點之具名繫結區段中的具名繫結執行個體。</span><span class="sxs-lookup"><span data-stu-id="09172-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="09172-132">在擷取的 MEX 中，繫結區段名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="09172-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="09172-133">在擷取的 MEX 中，合約的命名空間。</span><span class="sxs-lookup"><span data-stu-id="09172-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="09172-134">伺服器主要名稱 (SPN) 身分識別，用於與 MEX 端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="09172-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="09172-135">使用者主要名稱 (UPN) 身分識別，用於與 MEX 端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="09172-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="09172-136">DNS 身分識別，用於與 MEX 端點進行通訊。</span><span class="sxs-lookup"><span data-stu-id="09172-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="09172-137">指定要使用 "xml" 或 "datacontract" 序列化程式。</span><span class="sxs-lookup"><span data-stu-id="09172-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="09172-138">即使搭配整個 COM 架構用戶端使用，服務 Moniker 仍需要用戶端電腦上安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和支援的 .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="09172-138">Even when used with entirely COM-based clients, the service moniker requires [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="09172-139">此外，使用服務 Moniker 的用戶端應用程式也一定要載入適當版本的 .NET Framework 執行階段。</span><span class="sxs-lookup"><span data-stu-id="09172-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="09172-140">在 Office 應用程式中使用 Moniker 時，可能需要有組態檔來確認是否載入了正確的 Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="09172-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="09172-141">例如，在 Excel 中應將下列文字放入與 Excel.exe 檔案位在相同的目錄下，而且名為 Excel.exe.config 的檔案中：</span><span class="sxs-lookup"><span data-stu-id="09172-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="09172-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="09172-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="09172-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="09172-143">See Also</span></span>  
 [<span data-ttu-id="09172-144">如何：註冊和設定服務 Moniker</span><span class="sxs-lookup"><span data-stu-id="09172-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
