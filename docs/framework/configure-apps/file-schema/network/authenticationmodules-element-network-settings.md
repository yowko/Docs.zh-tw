---
title: <authenticationModules> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#authenticationModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules
helpviewer_keywords:
- authenticationModules element
- <authenticationModules> element
ms.assetid: 10fcfaad-82ef-4692-871a-0aec9dfbe75e
ms.openlocfilehash: 4fe44deba951e5302518ed855589ad1b0ca75343
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699526"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="57aac-102">@no__t 0authenticationModules > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="57aac-102">\<authenticationModules> Element (Network Settings)</span></span>
<span data-ttu-id="57aac-103">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="57aac-103">Specifies modules used to authenticate network requests.</span></span>  
  
[<span data-ttu-id="57aac-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="57aac-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="57aac-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="57aac-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="57aac-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<authenticationModules >**</span><span class="sxs-lookup"><span data-stu-id="57aac-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57aac-107">語法</span><span class="sxs-lookup"><span data-stu-id="57aac-107">Syntax</span></span>  
  
```xml  
<authenticationModules>   
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57aac-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57aac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="57aac-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="57aac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57aac-110">屬性</span><span class="sxs-lookup"><span data-stu-id="57aac-110">Attributes</span></span>  
 <span data-ttu-id="57aac-111">無。</span><span class="sxs-lookup"><span data-stu-id="57aac-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57aac-112">子元素</span><span class="sxs-lookup"><span data-stu-id="57aac-112">Child Elements</span></span>  
  
|<span data-ttu-id="57aac-113">**目**</span><span class="sxs-lookup"><span data-stu-id="57aac-113">**Element**</span></span>|<span data-ttu-id="57aac-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="57aac-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="57aac-115">add</span><span class="sxs-lookup"><span data-stu-id="57aac-115">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="57aac-116">將驗證模組新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="57aac-116">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="57aac-117">clear</span><span class="sxs-lookup"><span data-stu-id="57aac-117">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="57aac-118">清除應用程式中的所有驗證模組。</span><span class="sxs-lookup"><span data-stu-id="57aac-118">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="57aac-119">remove</span><span class="sxs-lookup"><span data-stu-id="57aac-119">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="57aac-120">從應用程式移除驗證模組。</span><span class="sxs-lookup"><span data-stu-id="57aac-120">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57aac-121">父項目</span><span class="sxs-lookup"><span data-stu-id="57aac-121">Parent Elements</span></span>  
  
|<span data-ttu-id="57aac-122">**目**</span><span class="sxs-lookup"><span data-stu-id="57aac-122">**Element**</span></span>|<span data-ttu-id="57aac-123">**描述**</span><span class="sxs-lookup"><span data-stu-id="57aac-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="57aac-124">system.net</span><span class="sxs-lookup"><span data-stu-id="57aac-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="57aac-125">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="57aac-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57aac-126">備註</span><span class="sxs-lookup"><span data-stu-id="57aac-126">Remarks</span></span>  
 <span data-ttu-id="57aac-127">@No__t-0 元素會指定用來進行伺服器驗證程式的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="57aac-127">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="57aac-128">驗證模組必須執行 0 @no__t 介面。</span><span class="sxs-lookup"><span data-stu-id="57aac-128">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="57aac-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="57aac-129">Configuration Files</span></span>  
 <span data-ttu-id="57aac-130">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="57aac-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57aac-131">範例</span><span class="sxs-lookup"><span data-stu-id="57aac-131">Example</span></span>  
 <span data-ttu-id="57aac-132">下列範例會啟用驗證模組。</span><span class="sxs-lookup"><span data-stu-id="57aac-132">The following example enables an authentication module.</span></span> <span data-ttu-id="57aac-133">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="57aac-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57aac-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57aac-134">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="57aac-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="57aac-135">Network Settings Schema</span></span>](index.md)
