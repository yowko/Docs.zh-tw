---
title: '&lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 1373d1e95a0e569f5e5cf433d305d008b4daf838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="6f3c9-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="6f3c9-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="6f3c9-103">設定用來加密和解密權杖的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="6f3c9-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="6f3c9-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="6f3c9-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="6f3c9-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="6f3c9-105">\<federationConfiguration></span></span>  
<span data-ttu-id="6f3c9-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="6f3c9-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f3c9-107">語法</span><span class="sxs-lookup"><span data-stu-id="6f3c9-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f3c9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6f3c9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6f3c9-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6f3c9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f3c9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6f3c9-110">Attributes</span></span>  
 <span data-ttu-id="6f3c9-111">無</span><span class="sxs-lookup"><span data-stu-id="6f3c9-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6f3c9-112">子元素</span><span class="sxs-lookup"><span data-stu-id="6f3c9-112">Child Elements</span></span>  
  
|<span data-ttu-id="6f3c9-113">項目</span><span class="sxs-lookup"><span data-stu-id="6f3c9-113">Element</span></span>|<span data-ttu-id="6f3c9-114">描述</span><span class="sxs-lookup"><span data-stu-id="6f3c9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f3c9-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="6f3c9-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="6f3c9-116">指定用來尋找和驗證 x.509 憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="6f3c9-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6f3c9-117">父項目</span><span class="sxs-lookup"><span data-stu-id="6f3c9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6f3c9-118">項目</span><span class="sxs-lookup"><span data-stu-id="6f3c9-118">Element</span></span>|<span data-ttu-id="6f3c9-119">描述</span><span class="sxs-lookup"><span data-stu-id="6f3c9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f3c9-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="6f3c9-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="6f3c9-121">包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="6f3c9-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6f3c9-122">範例</span><span class="sxs-lookup"><span data-stu-id="6f3c9-122">Example</span></span>  
 <span data-ttu-id="6f3c9-123">下列 XML 程式碼將示範如何使用\<serviceCertificate > 項目。</span><span class="sxs-lookup"><span data-stu-id="6f3c9-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="6f3c9-124">XML 取自`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="6f3c9-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
