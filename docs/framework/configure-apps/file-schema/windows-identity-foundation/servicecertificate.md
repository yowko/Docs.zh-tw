---
title: '&lt;serviceCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af59562dbf6c13970526f1665a9ba2c57c4f32ee
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766773"
---
# <a name="ltservicecertificategt"></a><span data-ttu-id="add71-102">&lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="add71-102">&lt;serviceCertificate&gt;</span></span>
<span data-ttu-id="add71-103">設定用來加密和解密權杖的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="add71-103">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="add71-104">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="add71-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="add71-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="add71-105">\<federationConfiguration></span></span>  
<span data-ttu-id="add71-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="add71-106">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add71-107">語法</span><span class="sxs-lookup"><span data-stu-id="add71-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="add71-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="add71-108">Attributes and Elements</span></span>  
 <span data-ttu-id="add71-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="add71-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="add71-110">屬性</span><span class="sxs-lookup"><span data-stu-id="add71-110">Attributes</span></span>  
 <span data-ttu-id="add71-111">無</span><span class="sxs-lookup"><span data-stu-id="add71-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="add71-112">子項目</span><span class="sxs-lookup"><span data-stu-id="add71-112">Child Elements</span></span>  
  
|<span data-ttu-id="add71-113">項目</span><span class="sxs-lookup"><span data-stu-id="add71-113">Element</span></span>|<span data-ttu-id="add71-114">描述</span><span class="sxs-lookup"><span data-stu-id="add71-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="add71-115">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="add71-115">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="add71-116">指定用來尋找和驗證 x.509 憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="add71-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="add71-117">父項目</span><span class="sxs-lookup"><span data-stu-id="add71-117">Parent Elements</span></span>  
  
|<span data-ttu-id="add71-118">項目</span><span class="sxs-lookup"><span data-stu-id="add71-118">Element</span></span>|<span data-ttu-id="add71-119">描述</span><span class="sxs-lookup"><span data-stu-id="add71-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="add71-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="add71-120">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="add71-121">包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="add71-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="add71-122">範例</span><span class="sxs-lookup"><span data-stu-id="add71-122">Example</span></span>  
 <span data-ttu-id="add71-123">下列 XML 程式碼將示範如何使用\<serviceCertificate > 項目。</span><span class="sxs-lookup"><span data-stu-id="add71-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="add71-124">XML 取自`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="add71-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
