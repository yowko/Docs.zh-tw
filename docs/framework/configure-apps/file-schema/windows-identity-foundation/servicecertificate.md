---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: ce8be6eea5469b099a368a0b62e791faa7e3cbfc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156988"
---
# \<serviceCertificate>

<span data-ttu-id="a27f9-101">設定用來加密和解密權杖的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="a27f9-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="a27f9-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a27f9-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a27f9-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a27f9-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a27f9-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a27f9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a27f9-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a27f9-105">Attributes</span></span>  

 <span data-ttu-id="a27f9-106">無</span><span class="sxs-lookup"><span data-stu-id="a27f9-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a27f9-107">子元素</span><span class="sxs-lookup"><span data-stu-id="a27f9-107">Child Elements</span></span>  
  
|<span data-ttu-id="a27f9-108">項目</span><span class="sxs-lookup"><span data-stu-id="a27f9-108">Element</span></span>|<span data-ttu-id="a27f9-109">描述</span><span class="sxs-lookup"><span data-stu-id="a27f9-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="a27f9-110">指定用來在憑證存放區中尋找並驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="a27f9-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a27f9-111">父項目</span><span class="sxs-lookup"><span data-stu-id="a27f9-111">Parent Elements</span></span>  
  
|<span data-ttu-id="a27f9-112">項目</span><span class="sxs-lookup"><span data-stu-id="a27f9-112">Element</span></span>|<span data-ttu-id="a27f9-113">描述</span><span class="sxs-lookup"><span data-stu-id="a27f9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="a27f9-114">包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 的設定。</span><span class="sxs-lookup"><span data-stu-id="a27f9-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a27f9-115">範例</span><span class="sxs-lookup"><span data-stu-id="a27f9-115">Example</span></span>  

 <span data-ttu-id="a27f9-116">下列 XML 會顯示元素的使用 \<serviceCertificate> 。</span><span class="sxs-lookup"><span data-stu-id="a27f9-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="a27f9-117">XML 取自 `CustomToken` 範例。</span><span class="sxs-lookup"><span data-stu-id="a27f9-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
