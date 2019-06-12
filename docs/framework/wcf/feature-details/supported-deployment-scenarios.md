---
title: 支援的部署案例： WCF
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 7b508f53365c1b4b90e2883ddb9d5f2a71c7e814
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025632"
---
# <a name="supported-deployment-scenarios"></a><span data-ttu-id="0ab75-102">支援的部署案例</span><span class="sxs-lookup"><span data-stu-id="0ab75-102">Supported deployment scenarios</span></span>

<span data-ttu-id="0ab75-103">支援在部分信任應用程式中使用的 Windows Communication Foundation (WCF) 功能子集主要被為了符合需求的部分，而不是全部使用 WCF 的案例。</span><span class="sxs-lookup"><span data-stu-id="0ab75-103">The subset of Windows Communication Foundation (WCF) features supported for use in partially trusted applications is designed to meet the requirements of some, but not all, scenarios for using WCF.</span></span> <span data-ttu-id="0ab75-104">在伺服器上，WCF 會符合網際網路範圍在 ASP.NET 2.0 中度信任權限執行第三方應用程式共用主控提供者設定基於安全性考量的需求。</span><span class="sxs-lookup"><span data-stu-id="0ab75-104">On the server, WCF meets the requirements of Internet-scale shared hosting providers who run third-party applications in the ASP.NET 2.0 Medium Trust permission set for security reasons.</span></span> <span data-ttu-id="0ab75-105">在用戶端，WCF 部分信任支援主要為了符合的部署技術需求這類[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)或[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的允許無接縫且安全的 XAML 瀏覽器應用程式技術從受信任的站台的桌面應用程式的部署。</span><span class="sxs-lookup"><span data-stu-id="0ab75-105">On the client, WCF partial trust support is designed to meet the requirements of deployment technologies such as [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]'s XAML Browser Application technology, which allow seamless and secure deployment of desktop applications from untrusted sites.</span></span>

## <a name="minimum-permission-requirements"></a><span data-ttu-id="0ab75-106">最小權限需求</span><span class="sxs-lookup"><span data-stu-id="0ab75-106">Minimum permission requirements</span></span>

<span data-ttu-id="0ab75-107">WCF 中其中一個下列標準具名權限集下執行應用程式支援功能的子集：</span><span class="sxs-lookup"><span data-stu-id="0ab75-107">WCF supports a subset of features in applications running under either of the following standard named permission sets:</span></span>

- <span data-ttu-id="0ab75-108">中度信任權限</span><span class="sxs-lookup"><span data-stu-id="0ab75-108">Medium Trust permissions</span></span>

- <span data-ttu-id="0ab75-109">網際網路區域權限</span><span class="sxs-lookup"><span data-stu-id="0ab75-109">Internet Zone permissions</span></span>

<span data-ttu-id="0ab75-110">嘗試在具有更嚴格的權限的部分信任應用程式中使用 WCF，可能會導致在執行階段的安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0ab75-110">Attempting to use WCF in partially trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>

<span data-ttu-id="0ab75-111">如需這些使用權限集合所支援之功能的詳細資訊，請參閱 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="0ab75-111">For more information about the features supported in these permission sets, see [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="partial-trust-on-the-server"></a><span data-ttu-id="0ab75-112">在伺服器上的部分信任</span><span class="sxs-lookup"><span data-stu-id="0ab75-112">Partial trust on the server</span></span>

<span data-ttu-id="0ab75-113">裝載服務的 ASP.NET Web 應用程式的許多商業的提供者託管其伺服器上執行的應用程式執行的 ASP.NET 2.0 中度信任權限集合中。</span><span class="sxs-lookup"><span data-stu-id="0ab75-113">Many commercial providers of ASP.NET Web application hosting services mandate that applications running on their servers run in the ASP.NET 2.0 Medium Trust permission set.</span></span> <span data-ttu-id="0ab75-114">前提是他們所使用，WCF 服務可以在這些環境中執行<xref:System.ServiceModel.BasicHttpBinding>，則<xref:System.ServiceModel.WebHttpBinding>，或<xref:System.ServiceModel.WSHttpBinding>具有傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="0ab75-114">WCF services can run in these environments provided they use the <xref:System.ServiceModel.BasicHttpBinding>, the <xref:System.ServiceModel.WebHttpBinding>, or the <xref:System.ServiceModel.WSHttpBinding> with transport-level security.</span></span>

<span data-ttu-id="0ab75-115">在中度信任裝載環境執行的 WCF 服務也可以藉由將訊息傳送至用戶端要求的回應中的其他伺服器做為中介層服務。</span><span class="sxs-lookup"><span data-stu-id="0ab75-115">WCF services running in Medium Trust hosting environments can also act as middle-tier services by sending messages to other servers in response to client requests.</span></span> <span data-ttu-id="0ab75-116">如果裝載的環境已經授與應用程式適當的 <xref:System.Net.WebPermission> 以便對目的伺服器發出傳出要求時，伺服器便會支援中介層案例。</span><span class="sxs-lookup"><span data-stu-id="0ab75-116">Middle-tier scenarios on the server are supported if the hosting environment has granted the application the appropriate <xref:System.Net.WebPermission> to make outbound requests to the desired server.</span></span>

<span data-ttu-id="0ab75-117">除了 SOAP 訊息使用其中一個支援的 SOAP 繫結，WCF 還支援<xref:System.ServiceModel.WebHttpBinding>建置部分信任的應用程式中的 Web 樣式服務。</span><span class="sxs-lookup"><span data-stu-id="0ab75-117">In addition to SOAP messaging using one of the supported SOAP bindings, WCF supports the <xref:System.ServiceModel.WebHttpBinding> for building Web-style services in partially trusted applications.</span></span> <span data-ttu-id="0ab75-118">[WCF Web HTTP 程式設計模型](wcf-web-http-programming-model.md)， [WCF 新聞訂閱](wcf-syndication.md)，並[AJAX 整合與 JSON 支援](ajax-integration-and-json-support.md)WCF 的功能支援在部分信任中。</span><span class="sxs-lookup"><span data-stu-id="0ab75-118">The [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md), [WCF Syndication](wcf-syndication.md), and [AJAX Integration and JSON Support](ajax-integration-and-json-support.md) features of WCF are all supported in partial trust.</span></span>

<span data-ttu-id="0ab75-119">工作流程服務需要完全信任使用權限，而且無法用在部分信任應用程式中。</span><span class="sxs-lookup"><span data-stu-id="0ab75-119">Workflow Services require Full Trust permissions and cannot be used in partially trusted applications.</span></span>

<span data-ttu-id="0ab75-120">如需詳細資訊，請參閱[如何：Use Medium Trust in ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=84603)。</span><span class="sxs-lookup"><span data-stu-id="0ab75-120">For more information, see [How to: Use Medium Trust in ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=84603).</span></span>

## <a name="partial-trust-on-the-client"></a><span data-ttu-id="0ab75-121">在用戶端上的部分信任</span><span class="sxs-lookup"><span data-stu-id="0ab75-121">Partial trust on the client</span></span>

<span data-ttu-id="0ab75-122">在從不受信任的網際網路網站中下載並執行程式碼時，必須採取特定的安全性預防措施。</span><span class="sxs-lookup"><span data-stu-id="0ab75-122">Certain security precautions must be taken when downloading and running code from untrusted Internet sites.</span></span> <span data-ttu-id="0ab75-123">[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) (英文) 和 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]的 XAML 瀏覽器應用程式 (XBAP) 技術兩者都會透過部分信任將有限的使用權限 (網際網路區域) 授與不受信任的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0ab75-123">Both [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) and [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)]'s XAML Browser Application (XBAP) technology make use of partial trust to grant limited permissions (Internet Zone) to untrusted code.</span></span>

<span data-ttu-id="0ab75-124">WCF 可以用來與從部分信任的應用程式透過下列方式部署的遠端伺服器通訊[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)或 XBAP。</span><span class="sxs-lookup"><span data-stu-id="0ab75-124">WCF can be used to communicate with remote servers from within partially trusted applications deployed by either [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or XBAP.</span></span> <span data-ttu-id="0ab75-125">網際網路區域權限集合包含<xref:System.Net.WebPermission>來源的主機，以允許這些應用程式使用任何支援中所述的 WCF 繫結與其來源伺服器與通訊[Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span><span class="sxs-lookup"><span data-stu-id="0ab75-125">The Internet Zone permission set includes <xref:System.Net.WebPermission> for the originating host, which allows these applications to communicate with their origin server using any of the supported WCF bindings described in [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0ab75-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ab75-126">See also</span></span>

- [<span data-ttu-id="0ab75-127">程式碼存取安全性</span><span class="sxs-lookup"><span data-stu-id="0ab75-127">Code Access Security</span></span>](../../misc/code-access-security.md)
- [<span data-ttu-id="0ab75-128">Windows Presentation Foundation 瀏覽器裝載的應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="0ab75-128">Windows Presentation Foundation Browser-Hosted Applications Overview</span></span>](../../wpf/app-development/wpf-xaml-browser-applications-overview.md)
- [<span data-ttu-id="0ab75-129">部分信任</span><span class="sxs-lookup"><span data-stu-id="0ab75-129">Partial Trust</span></span>](partial-trust.md)
- <span data-ttu-id="0ab75-130">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="0ab75-130">[ASP.NET Trust Levels and Policy Files](https://docs.microsoft.com/previous-versions/wyts434y(v=vs.140))</span></span>
