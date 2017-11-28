---
title: "HOW TO：將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d77e07cca938b67f5b79416ac4d8fdef96739ed2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a><span data-ttu-id="aca1a-102">HOW TO：將 ASP.NET Web 服務用戶端程式碼移轉至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="aca1a-102">How to: Migrate ASP.NET Web Service Client Code to the Windows Communication Foundation</span></span>
<span data-ttu-id="aca1a-103">下列程序描述將 ASP.NET Web 服務用戶端程式碼移轉至 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 所需要遵循的概略步驟。</span><span class="sxs-lookup"><span data-stu-id="aca1a-103">The following procedure describes the broad steps that need to be followed to migrate ASP.NET Web Service client code to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="aca1a-104">程序</span><span class="sxs-lookup"><span data-stu-id="aca1a-104">Procedure</span></span>  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a><span data-ttu-id="aca1a-105">將 ASP.NET Web 服務用戶端程式碼移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="aca1a-105">To migrate ASP.NET Web Service client code to WCF</span></span>  
  
1.  <span data-ttu-id="aca1a-106">請確定已存有用戶端的一組完整測試。</span><span class="sxs-lookup"><span data-stu-id="aca1a-106">Ensure that a comprehensive set of tests exist for the client.</span></span>  
  
2.  <span data-ttu-id="aca1a-107">使用 Visual Studio 2005 將用戶端應用程式升級到 .NET 2.0。</span><span class="sxs-lookup"><span data-stu-id="aca1a-107">Use Visual Studio 2005 to upgrade the client application to .NET 2.0.</span></span> <span data-ttu-id="aca1a-108">執行這組測試。</span><span class="sxs-lookup"><span data-stu-id="aca1a-108">Run the set of tests.</span></span>  
  
3.  <span data-ttu-id="aca1a-109">從用戶端專案移除 ASP.NET 用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="aca1a-109">Remove ASP.NET client code from the client project.</span></span> <span data-ttu-id="aca1a-110">該程式碼位於使用 WSDL.exe 工具產生的模組中。</span><span class="sxs-lookup"><span data-stu-id="aca1a-110">That code is in modules generated using the WSDL.exe tool.</span></span>  
  
4.  <span data-ttu-id="aca1a-111">產生[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]用戶端程式碼使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="aca1a-111">Generate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client code using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="aca1a-112">將程式碼新增至用戶端專案，然後將組態輸出合併至用戶端現有的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="aca1a-112">Add that code to the client project and merge the configuration output into the client’s existing configuration file.</span></span>  
  
5.  <span data-ttu-id="aca1a-113">編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="aca1a-113">Compile the application.</span></span> <span data-ttu-id="aca1a-114">將之前 ASP.NET 用戶端類型的參考取代為新 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類型的參考，以修復編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="aca1a-114">Repair the compilation errors by replacing references to the former ASP.NET client types with references to the new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client types.</span></span>  
  
6.  <span data-ttu-id="aca1a-115">執行這組測試。</span><span class="sxs-lookup"><span data-stu-id="aca1a-115">Run the set of tests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aca1a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aca1a-116">See Also</span></span>  
 [<span data-ttu-id="aca1a-117">如何： 將 ASP.NET Web 服務程式碼移轉至 Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="aca1a-117">How to: Migrate ASP.NET Web Service Code to the Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)
