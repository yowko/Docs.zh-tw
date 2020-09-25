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
ms.openlocfilehash: 154a73a5fe3fa9e2b6b1c9e5c462b76bdc1ba640
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201742"
---
# <a name="authenticationmodules-element-network-settings"></a><span data-ttu-id="0cc7a-102">\<authenticationModules> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="0cc7a-102">\<authenticationModules> Element (Network Settings)</span></span>

<span data-ttu-id="0cc7a-103">指定用來驗證網路要求的模組。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-103">Specifies modules used to authenticate network requests.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<authenticationModules>**

## <a name="syntax"></a><span data-ttu-id="0cc7a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0cc7a-104">Syntax</span></span>  
  
```xml  
<authenticationModules>
</authenticationModules>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cc7a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0cc7a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0cc7a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cc7a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0cc7a-107">Attributes</span></span>  

 <span data-ttu-id="0cc7a-108">無。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0cc7a-109">子元素</span><span class="sxs-lookup"><span data-stu-id="0cc7a-109">Child Elements</span></span>  
  
|<span data-ttu-id="0cc7a-110">**Element**</span><span class="sxs-lookup"><span data-stu-id="0cc7a-110">**Element**</span></span>|<span data-ttu-id="0cc7a-111">**說明**</span><span class="sxs-lookup"><span data-stu-id="0cc7a-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0cc7a-112">add</span><span class="sxs-lookup"><span data-stu-id="0cc7a-112">add</span></span>](add-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0cc7a-113">將驗證模組加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-113">Adds an authentication module to the application.</span></span>|  
|[<span data-ttu-id="0cc7a-114">清除</span><span class="sxs-lookup"><span data-stu-id="0cc7a-114">clear</span></span>](clear-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0cc7a-115">從應用程式清除所有驗證模組。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-115">Clears all authentication modules from the application.</span></span>|  
|[<span data-ttu-id="0cc7a-116">remove</span><span class="sxs-lookup"><span data-stu-id="0cc7a-116">remove</span></span>](remove-element-for-authenticationmodules-network-settings.md)|<span data-ttu-id="0cc7a-117">從應用程式移除驗證模組。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-117">Removes an authentication module from the application.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0cc7a-118">父項目</span><span class="sxs-lookup"><span data-stu-id="0cc7a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0cc7a-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="0cc7a-119">**Element**</span></span>|<span data-ttu-id="0cc7a-120">**說明**</span><span class="sxs-lookup"><span data-stu-id="0cc7a-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0cc7a-121">system.net</span><span class="sxs-lookup"><span data-stu-id="0cc7a-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="0cc7a-122">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cc7a-123">備註</span><span class="sxs-lookup"><span data-stu-id="0cc7a-123">Remarks</span></span>  

 <span data-ttu-id="0cc7a-124">專案 `authenticationModule` 會指定對伺服器進行驗證處理的驗證模組。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-124">The `authenticationModule` element specifies the authentication modules that conduct the authentication process with a server.</span></span> <span data-ttu-id="0cc7a-125">驗證模組必須執行 <xref:System.Net.IAuthenticationModule> 介面。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-125">An authentication module must implement the <xref:System.Net.IAuthenticationModule> interface.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0cc7a-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="0cc7a-126">Configuration Files</span></span>  

 <span data-ttu-id="0cc7a-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc7a-128">範例</span><span class="sxs-lookup"><span data-stu-id="0cc7a-128">Example</span></span>  

 <span data-ttu-id="0cc7a-129">下列範例會啟用驗證模組。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-129">The following example enables an authentication module.</span></span> <span data-ttu-id="0cc7a-130">您應該將 Version 和 PublicKeyToken 的值取代為指定模組的正確值。</span><span class="sxs-lookup"><span data-stu-id="0cc7a-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0cc7a-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cc7a-131">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="0cc7a-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0cc7a-132">Network Settings Schema</span></span>](index.md)
