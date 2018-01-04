---
title: "整合 COM 應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 130a7cda170721f34a5b44f3361bd591d6375267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="7c720-102">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="7c720-102">Integrating with COM Applications</span></span>
<span data-ttu-id="7c720-103">可以使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務 Moniker，將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務直接整合至現有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c720-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services can be integrated directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="7c720-104">服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。</span><span class="sxs-lookup"><span data-stu-id="7c720-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c720-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c720-105">In This Section</span></span>  
 [<span data-ttu-id="7c720-106">整合 COM+ 應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="7c720-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="7c720-107">提供整合處理序主要部分的概觀。</span><span class="sxs-lookup"><span data-stu-id="7c720-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="7c720-108">如何：註冊和設定服務 Moniker</span><span class="sxs-lookup"><span data-stu-id="7c720-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="7c720-109">若要在 COM 應用程式內使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker，請以 COM 登錄必要的屬性類型，並以必要的繫結組態設定 COM 應用程式和 Moniker。</span><span class="sxs-lookup"><span data-stu-id="7c720-109">To use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="7c720-110">如何：使用 Windows Communication Foundation 服務 Moniker 且不註冊</span><span class="sxs-lookup"><span data-stu-id="7c720-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="7c720-111">說明如何取得格式為 Web Services Definition Language (WSDL) 文件的合約定義，或如何從 WS-MetadataExchange 端點取得該定義。</span><span class="sxs-lookup"><span data-stu-id="7c720-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="7c720-112">如何：使用服務 Moniker 搭配 WSDL 合約</span><span class="sxs-lookup"><span data-stu-id="7c720-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="7c720-113">描述如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL Moniker 呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7c720-113">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span></span>  
  
 [<span data-ttu-id="7c720-114">如何：使用服務 Moniker 搭配中繼資料交換合約</span><span class="sxs-lookup"><span data-stu-id="7c720-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="7c720-115">描述如何使用指定 Mex 端點的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker 呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="7c720-115">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="7c720-116">如何：指定通道安全性認證</span><span class="sxs-lookup"><span data-stu-id="7c720-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="7c720-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker 支援 `IChannelCredentials` 介面，這個介面提供一系列的替代方法以指定通道認證。</span><span class="sxs-lookup"><span data-stu-id="7c720-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7c720-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="7c720-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="7c720-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c720-119">See Also</span></span>  
 [<span data-ttu-id="7c720-120">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="7c720-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
