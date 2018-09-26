---
title: '&lt;authenticationModules&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 394a686fe07036d6c3ac2bc51fb3503e1ee4a9e6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170804"
---
# <a name="ltauthenticationmodulesgt-element-network-settings"></a><span data-ttu-id="2f77d-102">&lt;authenticationModules&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="2f77d-102">&lt;authenticationModules&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2f77d-103">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="2f77d-103">Specifies modules used to authenticate network requests.</span></span>  
  
 <span data-ttu-id="2f77d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2f77d-104">\<configuration></span></span>  
<span data-ttu-id="2f77d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2f77d-105">\<system.net></span></span>  
<span data-ttu-id="2f77d-106">\<authenticationModules ></span><span class="sxs-lookup"><span data-stu-id="2f77d-106">\<authenticationModules></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f77d-107">語法</span><span class="sxs-lookup"><span data-stu-id="2f77d-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f77d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2f77d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2f77d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2f77d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f77d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2f77d-110">Attributes</span></span>  
 <span data-ttu-id="2f77d-111">無。</span><span class="sxs-lookup"><span data-stu-id="2f77d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2f77d-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2f77d-112">Child Elements</span></span>  
  
|<span data-ttu-id="2f77d-113">**目**</span><span class="sxs-lookup"><span data-stu-id="2f77d-113">**Element**</span></span>|<span data-ttu-id="2f77d-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="2f77d-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2f77d-115">add</span><span class="sxs-lookup"><span data-stu-id="2f77d-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="2f77d-116">將應用程式中的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="2f77d-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="2f77d-117">clear</span><span class="sxs-lookup"><span data-stu-id="2f77d-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="2f77d-118">清除所有的驗證模組，從應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f77d-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="2f77d-119">remove</span><span class="sxs-lookup"><span data-stu-id="2f77d-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="2f77d-120">移除應用程式中的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="2f77d-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f77d-121">父項目</span><span class="sxs-lookup"><span data-stu-id="2f77d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2f77d-122">**目**</span><span class="sxs-lookup"><span data-stu-id="2f77d-122">**Element**</span></span>|<span data-ttu-id="2f77d-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="2f77d-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2f77d-124">system.net</span><span class="sxs-lookup"><span data-stu-id="2f77d-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="2f77d-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="2f77d-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f77d-126">備註</span><span class="sxs-lookup"><span data-stu-id="2f77d-126">Remarks</span></span>  
 <span data-ttu-id="2f77d-127">`authenticationModule`項目會指定進行驗證程序與伺服器的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="2f77d-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="2f77d-128">驗證模組必須實作<xref:System.Net.IAuthenticationModule>介面。</span><span class="sxs-lookup"><span data-stu-id="2f77d-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2f77d-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="2f77d-129">Configuration Files</span></span>  
 <span data-ttu-id="2f77d-130">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="2f77d-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f77d-131">範例</span><span class="sxs-lookup"><span data-stu-id="2f77d-131">Example</span></span>  
 <span data-ttu-id="2f77d-132">下列範例會啟用驗證模組。</span><span class="sxs-lookup"><span data-stu-id="2f77d-132">The following example enables an authentication module.</span></span> <span data-ttu-id="2f77d-133">您應該取得版本和 PublicKeyToken 的值取代為正確的值，指定模組。</span><span class="sxs-lookup"><span data-stu-id="2f77d-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <add type="System.Net.DigestClient, System, Version=2.0.3600.0,  
                 Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f77d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f77d-134">See Also</span></span>  
 <xref:System.Net.IAuthenticationModule>  
 <xref:System.Net.AuthenticationManager>  
 [<span data-ttu-id="2f77d-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2f77d-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
