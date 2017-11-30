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
ms.openlocfilehash: 177639b973bf8c597bc8b994d37c99647c72feb8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="361cf-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="361cf-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="361cf-103">設定用來加密和解密權杖的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="361cf-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="361cf-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="361cf-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="361cf-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="361cf-105">\<federationConfiguration></span></span>  
<span data-ttu-id="361cf-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="361cf-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="361cf-107">語法</span><span class="sxs-lookup"><span data-stu-id="361cf-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="361cf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="361cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="361cf-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="361cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="361cf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="361cf-110">Attributes</span></span>  
 <span data-ttu-id="361cf-111">無</span><span class="sxs-lookup"><span data-stu-id="361cf-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="361cf-112">子元素</span><span class="sxs-lookup"><span data-stu-id="361cf-112">Child Elements</span></span>  
  
|<span data-ttu-id="361cf-113">項目</span><span class="sxs-lookup"><span data-stu-id="361cf-113">Element</span></span>|<span data-ttu-id="361cf-114">說明</span><span class="sxs-lookup"><span data-stu-id="361cf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="361cf-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="361cf-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="361cf-116">指定用來尋找和驗證 x.509 憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="361cf-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="361cf-117">父項目</span><span class="sxs-lookup"><span data-stu-id="361cf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="361cf-118">項目</span><span class="sxs-lookup"><span data-stu-id="361cf-118">Element</span></span>|<span data-ttu-id="361cf-119">說明</span><span class="sxs-lookup"><span data-stu-id="361cf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="361cf-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="361cf-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="361cf-121">包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="361cf-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="361cf-122">範例</span><span class="sxs-lookup"><span data-stu-id="361cf-122">Example</span></span>  
 <span data-ttu-id="361cf-123">下列 XML 程式碼將示範如何使用\<serviceCertificate > 項目。</span><span class="sxs-lookup"><span data-stu-id="361cf-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="361cf-124">XML 取自`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="361cf-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
