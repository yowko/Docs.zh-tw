---
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: 653dd9cfadbfd33f5371b77172199b946321bc8c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251862"
---
# \<serviceCertificate>
<span data-ttu-id="e6223-101">設定用來加密和解密權杖的 x.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="e6223-101">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="e6223-102">語法</span><span class="sxs-lookup"><span data-stu-id="e6223-102">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6223-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6223-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e6223-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e6223-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6223-105">屬性</span><span class="sxs-lookup"><span data-stu-id="e6223-105">Attributes</span></span>  
 <span data-ttu-id="e6223-106">無</span><span class="sxs-lookup"><span data-stu-id="e6223-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6223-107">子元素</span><span class="sxs-lookup"><span data-stu-id="e6223-107">Child Elements</span></span>  
  
|<span data-ttu-id="e6223-108">元素</span><span class="sxs-lookup"><span data-stu-id="e6223-108">Element</span></span>|<span data-ttu-id="e6223-109">描述</span><span class="sxs-lookup"><span data-stu-id="e6223-109">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="e6223-110">指定用來在憑證存放區中尋找和驗證 x.509 憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="e6223-110">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6223-111">父項目</span><span class="sxs-lookup"><span data-stu-id="e6223-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e6223-112">元素</span><span class="sxs-lookup"><span data-stu-id="e6223-112">Element</span></span>|<span data-ttu-id="e6223-113">描述</span><span class="sxs-lookup"><span data-stu-id="e6223-113">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="e6223-114">包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）的設定。</span><span class="sxs-lookup"><span data-stu-id="e6223-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6223-115">範例</span><span class="sxs-lookup"><span data-stu-id="e6223-115">Example</span></span>  
 <span data-ttu-id="e6223-116">下列 XML 顯示元素的用法 \<serviceCertificate> 。</span><span class="sxs-lookup"><span data-stu-id="e6223-116">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="e6223-117">XML 取自 `CustomToken` 範例。</span><span class="sxs-lookup"><span data-stu-id="e6223-117">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
