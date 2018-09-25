---
title: 建置第一個宣告感知 WCF 服務
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: e6324087afa62f276766c733284dc69e425b89bc
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078509"
---
# <a name="building-my-first-claims-aware-wcf-service"></a><span data-ttu-id="ff5f6-102">建置第一個宣告感知 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="ff5f6-102">Building My First Claims-Aware WCF Service</span></span>
## <a name="applies-to"></a><span data-ttu-id="ff5f6-103">適用於</span><span class="sxs-lookup"><span data-stu-id="ff5f6-103">Applies To</span></span>  
  
-   <span data-ttu-id="ff5f6-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="ff5f6-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="ff5f6-105">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="ff5f6-105">Windows Communication Foundation (WCF)</span></span>  
  
## <a name="overview"></a><span data-ttu-id="ff5f6-106">總覽</span><span class="sxs-lookup"><span data-stu-id="ff5f6-106">Overview</span></span>  
 <span data-ttu-id="ff5f6-107">本主題概述使用 WIF 建置宣告感知 WCF 服務的案例。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-107">This topic outlines the scenario of building claims-aware WCF services using WIF.</span></span> <span data-ttu-id="ff5f6-108">在一個宣告感知 Web 服務案例中，通常會有三個參與者：Web 服務本身、使用者和 Security Token Service (STS)。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-108">There are usually three participants in a claims-aware web service scenario: the web service itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="ff5f6-109">下列圖將說明這個案例：</span><span class="sxs-lookup"><span data-stu-id="ff5f6-109">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="ff5f6-110">![WIF 基本宣告感知 WCF 服務](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span><span class="sxs-lookup"><span data-stu-id="ff5f6-110">![WIF Basic Claims Aware WCF Service](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span></span>  
  
1.  <span data-ttu-id="ff5f6-111">WCF 服務用戶端 (有時稱為代理程式) 會使用 WIF 傳送認證至 STS，在驗證成功之後，STS 隨即發行權杖給代理程式。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-111">The WCF service client (sometimes called agent) uses WIF to send credentials to the STS and upon successful authentication, the agent is issued a token by the STS.</span></span>  
  
2.  <span data-ttu-id="ff5f6-112">代理程式隨即將 STS 發行的權杖傳送至 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-112">The agent sends this STS-issued token to the WCF service.</span></span>  
  
3.  <span data-ttu-id="ff5f6-113">宣告感知 WCF 服務設定為信任 STS 和它發行的權杖。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-113">The claims-aware WCF service is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="ff5f6-114">宣告感知 WCF 服務會使用 WIF 驗證和剖析權杖。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-114">The claims-aware WCF service uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="ff5f6-115">開發人員可以使用適當的 WIF API 和類型 (例如 **ClaimsPrincipal**) 來滿足應用程式的需求 (例如為它實作授權)。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="ff5f6-116">從 .NET 4.5 開始，WIF 是 .NET Framework 套件的一部分。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="ff5f6-117">在架構中直接提供 WIF 類別可讓 .NET 中的宣告式身分識別的整合更加深入，讓您更容易使用宣告。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="ff5f6-118">使用 WIF 4.5，您不必安裝任何超出範圍的元件就能開始開發宣告感知 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="ff5f6-119">WIF 類別現在已廣泛存在於各種組件，主要的類別是 System.Security.Claims、System.IdentityModel 和 System.IdentityModel.Services。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="ff5f6-120">STS 服務會在驗證成功後發行權杖。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="ff5f6-121">Microsoft 提供兩項業界標準 STS：</span><span class="sxs-lookup"><span data-stu-id="ff5f6-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   [<span data-ttu-id="ff5f6-122">Active Directory Federation Services (AD FS) 2.0</span><span class="sxs-lookup"><span data-stu-id="ff5f6-122">Active Directory Federation Services (AD FS) 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [<span data-ttu-id="ff5f6-123">Windows Azure 存取控制服務 (ACS)</span><span class="sxs-lookup"><span data-stu-id="ff5f6-123">Windows Azure Access Control Service (ACS)</span></span>](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 <span data-ttu-id="ff5f6-124">AD FS 2.0 是 Windows Server R2 的一部分，可以當做供內部部署案例使用的 STS；</span><span class="sxs-lookup"><span data-stu-id="ff5f6-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="ff5f6-125">Azure Active Directory 存取控制 (也稱為存取控制服務或 ACS) 是一項隨著 Microsoft Azure 提供的雲端服務。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-125">Azure Active Directory Access Control (also known as Access Control Service or ACS) is a cloud service, offered as part of Microsoft Azure.</span></span> <span data-ttu-id="ff5f6-126">此外，基於測試或教育目的，您也可以使用其他 STS 建立專屬宣告感知應用程式。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="ff5f6-127">例如，您可以使用屬於本機開發 STS [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849)這就是線上免費提供。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="ff5f6-128">若要建立第一個宣告感知 WCF 服務使用 WIF，請參閱[How To： 啟用 WCF Web 服務應用程式的 WIF](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ff5f6-128">To build your first claims-aware WCF service using WIF, see [How To: Enable WIF for a WCF Web Service Application](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ff5f6-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff5f6-129">See Also</span></span>  
 [<span data-ttu-id="ff5f6-130">開始使用 WIF</span><span class="sxs-lookup"><span data-stu-id="ff5f6-130">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
