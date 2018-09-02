---
title: 建置第一個宣告感知 ASP.NET Web 應用程式
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d889b0662d0b2df29b7e1e76e281c760c8965aac
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406218"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="f4f3e-102">建置第一個宣告感知 ASP.NET Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="f4f3e-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="f4f3e-103">適用於</span><span class="sxs-lookup"><span data-stu-id="f4f3e-103">Applies To</span></span>  
  
-   <span data-ttu-id="f4f3e-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="f4f3e-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="f4f3e-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f4f3e-105">ASP.NET</span></span>  
  
 <span data-ttu-id="f4f3e-106">本主題概述使用 WIF 建置宣告感知 ASP.NET Web 應用程式的案例。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="f4f3e-107">在一個宣告感知應用程式案例中，通常會有三個參與者：應用程式本身、終端使用者和 Security Token Service (STS)。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="f4f3e-108">下列圖將說明這個案例：</span><span class="sxs-lookup"><span data-stu-id="f4f3e-108">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="f4f3e-109">![WIF 基本 Web 應用程式](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span><span class="sxs-lookup"><span data-stu-id="f4f3e-109">![WIF Basic Web App](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span></span>  
  
1.  <span data-ttu-id="f4f3e-110">宣告感知應用程式使用 WIF 識別未驗證的要求，並將它們重新導向至 STS。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2.  <span data-ttu-id="f4f3e-111">使用者提供認證給 STS，一旦驗證成功，STS 就會發行權杖給使用者。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3.  <span data-ttu-id="f4f3e-112">使用者從 STS 重新導向至宣告感知應用程式，並且要求中已包含 STS 發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4.  <span data-ttu-id="f4f3e-113">宣告感知應用程式設定為信任 STS 和它發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="f4f3e-114">宣告感知應用程式會使用 WIF 驗證和剖析權杖。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="f4f3e-115">開發人員可以使用適當的 WIF API 和類型 (例如 **ClaimsPrincpal**) 來滿足應用程式的需求 (例如為它實作授權)。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincpal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="f4f3e-116">從 .NET 4.5 開始，WIF 是 .NET Framework 套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="f4f3e-117">在架構中直接提供 WIF 類別可讓 .NET 中的宣告式身分識別的整合更加深入，讓您更容易使用宣告。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="f4f3e-118">使用 WIF 4.5，您不必安裝任何超出範圍的元件就能開始開發宣告感知 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="f4f3e-119">WIF 類別現在已廣泛存在於各種組件，主要的類別是 System.Security.Claims、System.IdentityModel 和 System.IdentityModel.Services。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="f4f3e-120">STS 服務會在驗證成功後發行權杖。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="f4f3e-121">Microsoft 提供兩項業界標準 STS：</span><span class="sxs-lookup"><span data-stu-id="f4f3e-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   [<span data-ttu-id="f4f3e-122">Active Directory Federation Services (AD FS) 2.0</span><span class="sxs-lookup"><span data-stu-id="f4f3e-122">Active Directory Federation Services (AD FS) 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [<span data-ttu-id="f4f3e-123">Windows Azure 存取控制服務 (ACS)</span><span class="sxs-lookup"><span data-stu-id="f4f3e-123">Windows Azure Access Control Service (ACS)</span></span>](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 <span data-ttu-id="f4f3e-124">AD FS 2.0 是 Windows Server R2 的一部分，可以當做供內部部署案例使用的 STS；</span><span class="sxs-lookup"><span data-stu-id="f4f3e-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="f4f3e-125">ACS 則是當做 Microsoft Azure 平台的一部分而提供的雲端服務。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="f4f3e-126">此外，基於測試或教育目的，您也可以使用其他 STS 建立專屬宣告感知應用程式。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="f4f3e-127">例如，您可以使用屬於本機開發 STS [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849)這就是線上免費提供。</span><span class="sxs-lookup"><span data-stu-id="f4f3e-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="f4f3e-128">若要使用 WIF 建立您的第一個宣告感知 ASP.NET 應用程式，請遵循下列其中一項指示執行：</span><span class="sxs-lookup"><span data-stu-id="f4f3e-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
-   [<span data-ttu-id="f4f3e-129">操作說明：使用 WIF 建置宣告感知 ASP.NET MVC Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="f4f3e-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [<span data-ttu-id="f4f3e-130">操作說明：使用 WIF 建置宣告感知 ASP.NET Web Form 應用程式</span><span class="sxs-lookup"><span data-stu-id="f4f3e-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [<span data-ttu-id="f4f3e-131">操作說明：使用表單型驗證建置宣告感知 ASP.NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="f4f3e-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="f4f3e-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4f3e-132">See Also</span></span>  
 [<span data-ttu-id="f4f3e-133">開始使用 WIF</span><span class="sxs-lookup"><span data-stu-id="f4f3e-133">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
