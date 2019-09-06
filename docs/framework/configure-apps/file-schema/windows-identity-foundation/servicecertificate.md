---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251862"
---
# <a name="servicecertificate"></a><span data-ttu-id="a8fac-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a8fac-101">\<serviceCertificate></span></span>
<span data-ttu-id="a8fac-102">設定用來加密和解密權杖的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a8fac-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
<span data-ttu-id="a8fac-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a8fac-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a8fac-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="a8fac-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="a8fac-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="a8fac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="a8fac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCertificate >**</span><span class="sxs-lookup"><span data-stu-id="a8fac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8fac-107">語法</span><span class="sxs-lookup"><span data-stu-id="a8fac-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8fac-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a8fac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a8fac-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a8fac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8fac-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a8fac-110">Attributes</span></span>  
 <span data-ttu-id="a8fac-111">None</span><span class="sxs-lookup"><span data-stu-id="a8fac-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a8fac-112">子元素</span><span class="sxs-lookup"><span data-stu-id="a8fac-112">Child Elements</span></span>  
  
|<span data-ttu-id="a8fac-113">項目</span><span class="sxs-lookup"><span data-stu-id="a8fac-113">Element</span></span>|<span data-ttu-id="a8fac-114">描述</span><span class="sxs-lookup"><span data-stu-id="a8fac-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8fac-115">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="a8fac-115">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="a8fac-116">指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="a8fac-116">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8fac-117">父項目</span><span class="sxs-lookup"><span data-stu-id="a8fac-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a8fac-118">項目</span><span class="sxs-lookup"><span data-stu-id="a8fac-118">Element</span></span>|<span data-ttu-id="a8fac-119">描述</span><span class="sxs-lookup"><span data-stu-id="a8fac-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8fac-120">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="a8fac-120">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="a8fac-121">包含設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM） <xref:System.IdentityModel.Services.SessionAuthenticationModule>和（SAM）的設定。</span><span class="sxs-lookup"><span data-stu-id="a8fac-121">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a8fac-122">範例</span><span class="sxs-lookup"><span data-stu-id="a8fac-122">Example</span></span>  
 <span data-ttu-id="a8fac-123">下列 XML 顯示\<serviceCertificate > 元素的用法。</span><span class="sxs-lookup"><span data-stu-id="a8fac-123">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="a8fac-124">XML 取自`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="a8fac-124">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
