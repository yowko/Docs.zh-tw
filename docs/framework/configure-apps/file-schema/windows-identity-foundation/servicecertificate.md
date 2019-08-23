---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: a3aba5618855f7225dc8a427516eaa72b45f6e8b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942404"
---
# <a name="servicecertificate"></a><span data-ttu-id="d8761-101">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="d8761-101">\<serviceCertificate></span></span>
<span data-ttu-id="d8761-102">設定用來加密和解密權杖的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="d8761-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
 <span data-ttu-id="d8761-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="d8761-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="d8761-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="d8761-104">\<federationConfiguration></span></span>  
<span data-ttu-id="d8761-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="d8761-105">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8761-106">語法</span><span class="sxs-lookup"><span data-stu-id="d8761-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8761-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8761-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d8761-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8761-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8761-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d8761-109">Attributes</span></span>  
 <span data-ttu-id="d8761-110">None</span><span class="sxs-lookup"><span data-stu-id="d8761-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d8761-111">子元素</span><span class="sxs-lookup"><span data-stu-id="d8761-111">Child Elements</span></span>  
  
|<span data-ttu-id="d8761-112">項目</span><span class="sxs-lookup"><span data-stu-id="d8761-112">Element</span></span>|<span data-ttu-id="d8761-113">描述</span><span class="sxs-lookup"><span data-stu-id="d8761-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8761-114">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="d8761-114">\<certificateReference></span></span>](certificatereference.md)|<span data-ttu-id="d8761-115">指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="d8761-115">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d8761-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d8761-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d8761-117">項目</span><span class="sxs-lookup"><span data-stu-id="d8761-117">Element</span></span>|<span data-ttu-id="d8761-118">說明</span><span class="sxs-lookup"><span data-stu-id="d8761-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8761-119">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="d8761-119">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="d8761-120">包含設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule>和 (SAM) 的設定。</span><span class="sxs-lookup"><span data-stu-id="d8761-120">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d8761-121">範例</span><span class="sxs-lookup"><span data-stu-id="d8761-121">Example</span></span>  
 <span data-ttu-id="d8761-122">下列 XML 顯示\<serviceCertificate > 元素的用法。</span><span class="sxs-lookup"><span data-stu-id="d8761-122">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="d8761-123">XML 取自`CustomToken`範例。</span><span class="sxs-lookup"><span data-stu-id="d8761-123">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
