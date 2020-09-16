---
title: 支援的部署案例
ms.date: 03/30/2017
ms.assetid: 3399f208-3504-4c70-a22e-a7c02a8b94a6
ms.openlocfilehash: 299c8f2e29806a123e0a8b6e1e70d8cc13daa7bf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546246"
---
# <a name="supported-deployment-scenarios"></a><span data-ttu-id="91e41-102">支援的部署案例</span><span class="sxs-lookup"><span data-stu-id="91e41-102">Supported deployment scenarios</span></span>

<span data-ttu-id="91e41-103">支援在部分信任應用程式中使用 Windows Communication Foundation (WCF) 功能的子集，是為了滿足使用 WCF 的部分（而非全部）案例的需求而設計。</span><span class="sxs-lookup"><span data-stu-id="91e41-103">The subset of Windows Communication Foundation (WCF) features supported for use in partially trusted applications is designed to meet the requirements of some, but not all, scenarios for using WCF.</span></span> <span data-ttu-id="91e41-104">在伺服器上，WCF 符合網際網路規模的共用主機服務提供者需求，這些提供者會基於安全性理由，在 ASP.NET 2.0 中信任許可權集合中執行協力廠商應用程式。</span><span class="sxs-lookup"><span data-stu-id="91e41-104">On the server, WCF meets the requirements of Internet-scale shared hosting providers who run third-party applications in the ASP.NET 2.0 Medium Trust permission set for security reasons.</span></span> <span data-ttu-id="91e41-105">在用戶端上，WCF 部分信任支援的設計是為了滿足部署技術的需求，例如 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) 或 WPF 的 XAML 瀏覽器應用程式技術，可讓您從不受信任的網站進行無縫且安全的桌面應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="91e41-105">On the client, WCF partial trust support is designed to meet the requirements of deployment technologies such as [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or WPF's XAML Browser Application technology, which allow seamless and secure deployment of desktop applications from untrusted sites.</span></span>

## <a name="minimum-permission-requirements"></a><span data-ttu-id="91e41-106">最低許可權需求</span><span class="sxs-lookup"><span data-stu-id="91e41-106">Minimum permission requirements</span></span>

<span data-ttu-id="91e41-107">WCF 支援應用程式中，以下列其中一個標準命名許可權集合執行的功能子集：</span><span class="sxs-lookup"><span data-stu-id="91e41-107">WCF supports a subset of features in applications running under either of the following standard named permission sets:</span></span>

- <span data-ttu-id="91e41-108">中度信任權限</span><span class="sxs-lookup"><span data-stu-id="91e41-108">Medium Trust permissions</span></span>

- <span data-ttu-id="91e41-109">網際網路區域權限</span><span class="sxs-lookup"><span data-stu-id="91e41-109">Internet Zone permissions</span></span>

<span data-ttu-id="91e41-110">在部分信任的應用程式中嘗試使用具有較嚴格許可權的 WCF，可能會在執行時間導致安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="91e41-110">Attempting to use WCF in partially trusted applications with more restrictive permissions may result in security exceptions at runtime.</span></span>

<span data-ttu-id="91e41-111">如需這些使用權限集合所支援之功能的詳細資訊，請參閱 [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="91e41-111">For more information about the features supported in these permission sets, see [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="partial-trust-on-the-server"></a><span data-ttu-id="91e41-112">伺服器上的部分信任</span><span class="sxs-lookup"><span data-stu-id="91e41-112">Partial trust on the server</span></span>

<span data-ttu-id="91e41-113">ASP.NET Web 應用程式裝載服務的許多商業提供者都要求在其伺服器上執行的應用程式會以 ASP.NET 2.0 中度信任許可權集合執行。</span><span class="sxs-lookup"><span data-stu-id="91e41-113">Many commercial providers of ASP.NET Web application hosting services mandate that applications running on their servers run in the ASP.NET 2.0 Medium Trust permission set.</span></span> <span data-ttu-id="91e41-114">WCF 服務可以在這些環境中執行，前提是它們使用 <xref:System.ServiceModel.BasicHttpBinding> 、 <xref:System.ServiceModel.WebHttpBinding> 或搭配 <xref:System.ServiceModel.WSHttpBinding> 傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="91e41-114">WCF services can run in these environments provided they use the <xref:System.ServiceModel.BasicHttpBinding>, the <xref:System.ServiceModel.WebHttpBinding>, or the <xref:System.ServiceModel.WSHttpBinding> with transport-level security.</span></span>

<span data-ttu-id="91e41-115">在中度信任主機環境中執行的 WCF 服務，也可以藉由將訊息傳送至其他伺服器來回應用戶端要求，以作為中介層服務。</span><span class="sxs-lookup"><span data-stu-id="91e41-115">WCF services running in Medium Trust hosting environments can also act as middle-tier services by sending messages to other servers in response to client requests.</span></span> <span data-ttu-id="91e41-116">如果裝載的環境已經授與應用程式適當的 <xref:System.Net.WebPermission> 以便對目的伺服器發出傳出要求時，伺服器便會支援中介層案例。</span><span class="sxs-lookup"><span data-stu-id="91e41-116">Middle-tier scenarios on the server are supported if the hosting environment has granted the application the appropriate <xref:System.Net.WebPermission> to make outbound requests to the desired server.</span></span>

<span data-ttu-id="91e41-117">除了使用其中一個支援之 SOAP 系結的 SOAP 訊息之外，WCF 支援在 <xref:System.ServiceModel.WebHttpBinding> 部分信任的應用程式中建立 Web 樣式服務。</span><span class="sxs-lookup"><span data-stu-id="91e41-117">In addition to SOAP messaging using one of the supported SOAP bindings, WCF supports the <xref:System.ServiceModel.WebHttpBinding> for building Web-style services in partially trusted applications.</span></span> <span data-ttu-id="91e41-118">Wcf [WEB HTTP 程式設計模型](wcf-web-http-programming-model.md)、 [wcf 摘要整合](wcf-syndication.md)，以及 wcf 的 [AJAX 整合與 JSON 支援](ajax-integration-and-json-support.md) 功能全都在部分信任中受到支援。</span><span class="sxs-lookup"><span data-stu-id="91e41-118">The [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md), [WCF Syndication](wcf-syndication.md), and [AJAX Integration and JSON Support](ajax-integration-and-json-support.md) features of WCF are all supported in partial trust.</span></span>

<span data-ttu-id="91e41-119">工作流程服務需要完全信任使用權限，而且無法用在部分信任應用程式中。</span><span class="sxs-lookup"><span data-stu-id="91e41-119">Workflow Services require Full Trust permissions and cannot be used in partially trusted applications.</span></span>

<span data-ttu-id="91e41-120">如需詳細資訊，請參閱 [如何：在 ASP.NET 2.0 中使用中度信任](/previous-versions/msp-n-p/ff648344(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="91e41-120">For more information, see [How to: Use Medium Trust in ASP.NET 2.0](/previous-versions/msp-n-p/ff648344(v=pandp.10)).</span></span>

## <a name="partial-trust-on-the-client"></a><span data-ttu-id="91e41-121">用戶端上的部分信任</span><span class="sxs-lookup"><span data-stu-id="91e41-121">Partial trust on the client</span></span>

<span data-ttu-id="91e41-122">在從不受信任的網際網路網站中下載並執行程式碼時，必須採取特定的安全性預防措施。</span><span class="sxs-lookup"><span data-stu-id="91e41-122">Certain security precautions must be taken when downloading and running code from untrusted Internet sites.</span></span> <span data-ttu-id="91e41-123">[ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment)和 WPF 的 XAML 瀏覽器應用程式 (XBAP) 技術都利用部分信任將有限的許可權授與不受信任的程式碼 (網際網路區域) 。</span><span class="sxs-lookup"><span data-stu-id="91e41-123">Both [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) and WPF's XAML Browser Application (XBAP) technology make use of partial trust to grant limited permissions (Internet Zone) to untrusted code.</span></span>

<span data-ttu-id="91e41-124">WCF 可以用來在 [ClickOnce 部署](/visualstudio/deployment/clickonce-security-and-deployment) 或 XBAP 所部署的部分信任應用程式中，與遠端伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="91e41-124">WCF can be used to communicate with remote servers from within partially trusted applications deployed by either [ClickOnce Deployment](/visualstudio/deployment/clickonce-security-and-deployment) or XBAP.</span></span> <span data-ttu-id="91e41-125">網際網路區域許可權集合包含 <xref:System.Net.WebPermission> 來源主機的，可讓這些應用程式使用 [部分信任功能相容性](partial-trust-feature-compatibility.md)中所述的任何支援 WCF 系結來與其源伺服器通訊。</span><span class="sxs-lookup"><span data-stu-id="91e41-125">The Internet Zone permission set includes <xref:System.Net.WebPermission> for the originating host, which allows these applications to communicate with their origin server using any of the supported WCF bindings described in [Partial Trust Feature Compatibility](partial-trust-feature-compatibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91e41-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e41-126">See also</span></span>

- [<span data-ttu-id="91e41-127">代碼啟用安全性</span><span class="sxs-lookup"><span data-stu-id="91e41-127">Code Access Security</span></span>](../../misc/code-access-security.md)
- [<span data-ttu-id="91e41-128">Windows Presentation Foundation 瀏覽器裝載的應用程式概觀</span><span class="sxs-lookup"><span data-stu-id="91e41-128">Windows Presentation Foundation Browser-Hosted Applications Overview</span></span>](/dotnet/desktop/wpf/app-development/wpf-xaml-browser-applications-overview)
- [<span data-ttu-id="91e41-129">部分信任</span><span class="sxs-lookup"><span data-stu-id="91e41-129">Partial Trust</span></span>](partial-trust.md)
- <span data-ttu-id="91e41-130">[ASP.NET Trust Levels and Policy Files](/previous-versions/wyts434y(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="91e41-130">[ASP.NET Trust Levels and Policy Files](/previous-versions/wyts434y(v=vs.140))</span></span>
