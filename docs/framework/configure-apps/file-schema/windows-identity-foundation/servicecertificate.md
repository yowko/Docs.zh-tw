---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 328d074f9edc5ddf871308a7e3d694bf94adea78
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261596"
---
# <a name="servicecertificate"></a><span data-ttu-id="b8f4f-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="b8f4f-101">\<serviceCertificate></span></span>
<span data-ttu-id="b8f4f-102">設定用來加密和解密權杖的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="b8f4f-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="b8f4f-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="b8f4f-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="b8f4f-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="b8f4f-104">\<federationConfiguration></span></span>  
<span data-ttu-id="b8f4f-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="b8f4f-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f4f-106">語法</span><span class="sxs-lookup"><span data-stu-id="b8f4f-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8f4f-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8f4f-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b8f4f-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8f4f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8f4f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="b8f4f-109">Attributes</span></span>  
 <span data-ttu-id="b8f4f-110">無</span><span class="sxs-lookup"><span data-stu-id="b8f4f-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8f4f-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b8f4f-111">Child Elements</span></span>  
  
|<span data-ttu-id="b8f4f-112">項目</span><span class="sxs-lookup"><span data-stu-id="b8f4f-112">Element</span></span>|<span data-ttu-id="b8f4f-113">描述</span><span class="sxs-lookup"><span data-stu-id="b8f4f-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8f4f-114">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="b8f4f-114">\<certificateReference></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatereference.md)|<span data-ttu-id="b8f4f-115">指定用來尋找和驗證 X.509 憑證的憑證存放區中的設定。</span><span class="sxs-lookup"><span data-stu-id="b8f4f-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8f4f-116">父項目</span><span class="sxs-lookup"><span data-stu-id="b8f4f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b8f4f-117">項目</span><span class="sxs-lookup"><span data-stu-id="b8f4f-117">Element</span></span>|<span data-ttu-id="b8f4f-118">描述</span><span class="sxs-lookup"><span data-stu-id="b8f4f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8f4f-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="b8f4f-119">\<federationConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|<span data-ttu-id="b8f4f-120">包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="b8f4f-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b8f4f-121">範例</span><span class="sxs-lookup"><span data-stu-id="b8f4f-121">Example</span></span>  
 <span data-ttu-id="b8f4f-122">下列 XML 示範如何使用\<v > 項目。</span><span class="sxs-lookup"><span data-stu-id="b8f4f-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="b8f4f-123">XML 取自`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="b8f4f-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
