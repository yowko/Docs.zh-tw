---
title: WIF API 參考
ms.date: 03/30/2017
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
author: BrucePerlerMS
ms.openlocfilehash: 17a1da0a3b0ea6567fd805e7273f793ace35ae69
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958350"
---
# <a name="wif-api-reference"></a><span data-ttu-id="430fc-102">WIF API 參考</span><span class="sxs-lookup"><span data-stu-id="430fc-102">WIF API Reference</span></span>
<span data-ttu-id="430fc-103">Windows Identity Foundation (WIF) 類別會分成下列組件：`mscorlib` (mscorlib.dll)、`System.IdentityModel` (System.IdentityModel.dll)、`System.IdentityModel.Services` (System.IdentityModel.Services.dll) 和 `System.ServiceModel` (System.ServiceModel.dll)。</span><span class="sxs-lookup"><span data-stu-id="430fc-103">Windows Identity Foundation (WIF) classes are split across the following assemblies: `mscorlib` (mscorlib.dll), `System.IdentityModel` (System.IdentityModel.dll), `System.IdentityModel.Services` (System.IdentityModel.Services.dll), and `System.ServiceModel` (System.ServiceModel.dll).</span></span> <span data-ttu-id="430fc-104">本主題提供 WIF 命名空間的連結，以及每個命名空間所包含類別的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="430fc-104">This topic provides links to the WIF namespaces and brief explanations of the classes that each namespace contains.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="430fc-105">下列 `System.IdentityModel` 命名空間包含的類別可實作 WCF 宣告式身分識別模型：<xref:System.IdentityModel.Claims?displayProperty=nameWithType>、<xref:System.IdentityModel.Policy?displayProperty=nameWithType> 和 <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="430fc-105">The following `System.IdentityModel` namespaces contain classes that implement the WCF claims-based identity model: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, and <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>.</span></span> <span data-ttu-id="430fc-106">從 .NET Framework 4.5 開始，WIF 已取代 WCF 宣告式身分識別模型。</span><span class="sxs-lookup"><span data-stu-id="430fc-106">Starting with .NET Framework 4.5, the WCF claims-based identity model is superseded by WIF.</span></span> <span data-ttu-id="430fc-107">在建置以 WIF 為基礎的方案時，您不應該使用這三個命名空間中的類別。</span><span class="sxs-lookup"><span data-stu-id="430fc-107">You should not use classes in these three namespaces when building solutions based on WIF.</span></span>  
  
 <xref:System.IdentityModel?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-108">包含的類別代表 Cookie 轉換、安全性權杖服務，以及特定的 XML 字典讀取器。</span><span class="sxs-lookup"><span data-stu-id="430fc-108">Contains classes that represent cookie transforms, security token services, and specialized XML dictionary readers.</span></span>  
  
 <xref:System.IdentityModel.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-109">包含的類別可為使用 Windows Identity Foundation (WIF) 建置的應用程式和服務提供組態。</span><span class="sxs-lookup"><span data-stu-id="430fc-109">Contains classes that provide configuration for applications and services built using the Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="430fc-110">此命名空間中的類別代表 [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 元素下的設定。</span><span class="sxs-lookup"><span data-stu-id="430fc-110">The classes in this namespace represent settings under the [\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
 <xref:System.IdentityModel.Metadata?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-111">包含的類別代表同盟中繼資料文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="430fc-111">Contains classes that represent elements in a Federation Metadata document.</span></span>  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-112">包含的類別代表 WS-Trust 成品。</span><span class="sxs-lookup"><span data-stu-id="430fc-112">Contains classes that represent WS-Trust artifacts.</span></span>  
  
 <xref:System.IdentityModel.Services?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-113">包含的類別用於被動 (WS-同盟) 情節。</span><span class="sxs-lookup"><span data-stu-id="430fc-113">Contains classes that are used in passive (WS-Federation) scenarios.</span></span> <span data-ttu-id="430fc-114">也包含一些代表 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 元素下設定的類別。</span><span class="sxs-lookup"><span data-stu-id="430fc-114">Also contains some classes that represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="430fc-115">此元素下的設定可用來設定應用程式的 WS-同盟。</span><span class="sxs-lookup"><span data-stu-id="430fc-115">Settings under this element configure WS-Federation for applications.</span></span> <span data-ttu-id="430fc-116">`System.IdentityModel.Services.Configuration` 命名空間包含大部分用來設定 WS-同盟的類別。</span><span class="sxs-lookup"><span data-stu-id="430fc-116">The `System.IdentityModel.Services.Configuration` namespace contains most of the classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-117">包含的類別可為使用 WS-同盟通訊協定的 WIF 應用程式提供組態。</span><span class="sxs-lookup"><span data-stu-id="430fc-117">Contains classes that provide configuration for WIF applications that use the WS-Federation protocol.</span></span> <span data-ttu-id="430fc-118">此命名空間中的類別代表 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 元素下的設定。</span><span class="sxs-lookup"><span data-stu-id="430fc-118">The classes in this namespace represent settings under the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) element.</span></span> <span data-ttu-id="430fc-119">`System.IdentityModel.Services` 命名空間也包含一些用來設定 WS-同盟的類別。</span><span class="sxs-lookup"><span data-stu-id="430fc-119">The `System.IdentityModel.Services` namespace also contains some classes that are used to configure WS-Federation.</span></span>  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-120">包含適用於 Web 伺服陣列情節的特定安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="430fc-120">Contains specialized security token handlers for Web farm scenarios.</span></span>  
  
 <xref:System.IdentityModel.Tokens?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-121">包含的類別代表安全性權杖、安全性權杖處理常式，以及其他安全性權杖成品。</span><span class="sxs-lookup"><span data-stu-id="430fc-121">Contains classes that represent security tokens, security token handlers, and other security token artifacts.</span></span>  
  
 <xref:System.Security.Claims?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-122">包含的類別代表宣告、宣告式身分識別、宣告式主體，以及其他宣告式身分識別模型成品。</span><span class="sxs-lookup"><span data-stu-id="430fc-122">Contains classes that represent claims, claims-based identities, claims-based principals, and other claims-based identity model artifacts.</span></span>  
  
 <xref:System.ServiceModel.Security?displayProperty=nameWithType>  
 <span data-ttu-id="430fc-123">包含的類別代表 WCF 合約、通道、服務主機，以及主動 (WS-Trust) 情節中使用的其他成品。</span><span class="sxs-lookup"><span data-stu-id="430fc-123">Contains classes that represent WCF contracts, channels, service hosts and other artifacts that are used in active (WS-Trust) scenarios.</span></span> <span data-ttu-id="430fc-124">此命名空間也包含專屬於 Windows Communication Foundation (WCF) 而不會由 WIF 使用的類別。</span><span class="sxs-lookup"><span data-stu-id="430fc-124">This namespace also contains classes that are specific to Windows Communication Foundation (WCF) and that are not used by WIF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430fc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="430fc-125">See also</span></span>

- [<span data-ttu-id="430fc-126">WIF 組態參考</span><span class="sxs-lookup"><span data-stu-id="430fc-126">WIF Configuration Reference</span></span>](../../../docs/framework/security/wif-configuration-reference.md)
- [<span data-ttu-id="430fc-127">WIF 3.5 和 WIF 4.5 之間的命名空間對應</span><span class="sxs-lookup"><span data-stu-id="430fc-127">Namespace Mapping between WIF 3.5 and WIF 4.5</span></span>](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
