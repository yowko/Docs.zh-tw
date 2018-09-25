---
title: '&lt;ServiceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 008d2269a72759117658e27ec130cc8cf62cfdfa
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084302"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="c94a4-102">&lt;ServiceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="c94a4-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="c94a4-103">設定用來加密和解密權杖的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="c94a4-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="c94a4-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="c94a4-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="c94a4-105">\<Federationconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="c94a4-105">\<federationConfiguration></span></span>  
<span data-ttu-id="c94a4-106">\<v ></span><span class="sxs-lookup"><span data-stu-id="c94a4-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94a4-107">語法</span><span class="sxs-lookup"><span data-stu-id="c94a4-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c94a4-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c94a4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c94a4-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c94a4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c94a4-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c94a4-110">Attributes</span></span>  
 <span data-ttu-id="c94a4-111">無</span><span class="sxs-lookup"><span data-stu-id="c94a4-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c94a4-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c94a4-112">Child Elements</span></span>  
  
|<span data-ttu-id="c94a4-113">項目</span><span class="sxs-lookup"><span data-stu-id="c94a4-113">Element</span></span>|<span data-ttu-id="c94a4-114">描述</span><span class="sxs-lookup"><span data-stu-id="c94a4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c94a4-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="c94a4-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="c94a4-116">指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="c94a4-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c94a4-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c94a4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c94a4-118">項目</span><span class="sxs-lookup"><span data-stu-id="c94a4-118">Element</span></span>|<span data-ttu-id="c94a4-119">描述</span><span class="sxs-lookup"><span data-stu-id="c94a4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c94a4-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="c94a4-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="c94a4-121">包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="c94a4-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c94a4-122">範例</span><span class="sxs-lookup"><span data-stu-id="c94a4-122">Example</span></span>  
 <span data-ttu-id="c94a4-123">下列 XML 示範如何使用\<v > 項目。</span><span class="sxs-lookup"><span data-stu-id="c94a4-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="c94a4-124">XML 取自`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="c94a4-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
