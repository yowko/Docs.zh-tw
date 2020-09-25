---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 216b4c73e06469d6577c61338ad1af0fdd2dc05e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185570"
---
# \<system.identityModel>

<span data-ttu-id="78c32-102">提供在應用程式中啟用 Windows Identity Foundation (WIF) 選項的設定。</span><span class="sxs-lookup"><span data-stu-id="78c32-102">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel>**  
  
## <a name="syntax"></a><span data-ttu-id="78c32-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="78c32-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78c32-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="78c32-104">Attributes and Elements</span></span>  

 <span data-ttu-id="78c32-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="78c32-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78c32-106">屬性</span><span class="sxs-lookup"><span data-stu-id="78c32-106">Attributes</span></span>  

 <span data-ttu-id="78c32-107">無</span><span class="sxs-lookup"><span data-stu-id="78c32-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78c32-108">子元素</span><span class="sxs-lookup"><span data-stu-id="78c32-108">Child Elements</span></span>  
  
|<span data-ttu-id="78c32-109">項目</span><span class="sxs-lookup"><span data-stu-id="78c32-109">Element</span></span>|<span data-ttu-id="78c32-110">描述</span><span class="sxs-lookup"><span data-stu-id="78c32-110">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="78c32-111">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="78c32-111">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78c32-112">父項目</span><span class="sxs-lookup"><span data-stu-id="78c32-112">Parent Elements</span></span>  
  
|<span data-ttu-id="78c32-113">項目</span><span class="sxs-lookup"><span data-stu-id="78c32-113">Element</span></span>|<span data-ttu-id="78c32-114">描述</span><span class="sxs-lookup"><span data-stu-id="78c32-114">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="78c32-115">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="78c32-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78c32-116">備註</span><span class="sxs-lookup"><span data-stu-id="78c32-116">Remarks</span></span>  

 <span data-ttu-id="78c32-117">將區段新增至 `<system.identityModel>` 設定檔，以將服務或應用程式設定為使用 Windows Identity Foundation (WIF) 。</span><span class="sxs-lookup"><span data-stu-id="78c32-117">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="78c32-118">`<system.identityModel>`元素是由 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="78c32-118">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78c32-119">範例</span><span class="sxs-lookup"><span data-stu-id="78c32-119">Example</span></span>  

 <span data-ttu-id="78c32-120">下列範例顯示如何將 `<system.identityModel>` 區段新增至設定檔。</span><span class="sxs-lookup"><span data-stu-id="78c32-120">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="78c32-121">您必須先在元素底下加入設定區段和命名空間宣告 `<configSections>` 。</span><span class="sxs-lookup"><span data-stu-id="78c32-121">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="78c32-122">然後，您可以將專案新增 `<system.IdentityModel>` 至您的設定檔，以指定一或多個身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="78c32-122">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="78c32-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78c32-123">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
