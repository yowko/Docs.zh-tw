---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: a54f5ce86aee1a5e831c0b10aa1471d4a82f40a5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251798"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="f3196-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f3196-102">\<system.identityModel></span></span>
<span data-ttu-id="f3196-103">提供在應用程式中啟用 Windows Identity Foundation （WIF）選項的設定。</span><span class="sxs-lookup"><span data-stu-id="f3196-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
<span data-ttu-id="f3196-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3196-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3196-105">&nbsp;&nbsp; **\<Microsoft.identitymodel >**</span><span class="sxs-lookup"><span data-stu-id="f3196-105">&nbsp;&nbsp;**\<system.identityModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3196-106">語法</span><span class="sxs-lookup"><span data-stu-id="f3196-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3196-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f3196-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f3196-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f3196-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3196-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f3196-109">Attributes</span></span>  
 <span data-ttu-id="f3196-110">無</span><span class="sxs-lookup"><span data-stu-id="f3196-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f3196-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f3196-111">Child Elements</span></span>  
  
|<span data-ttu-id="f3196-112">項目</span><span class="sxs-lookup"><span data-stu-id="f3196-112">Element</span></span>|<span data-ttu-id="f3196-113">描述</span><span class="sxs-lookup"><span data-stu-id="f3196-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3196-114">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f3196-114">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="f3196-115">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="f3196-115">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3196-116">父項目</span><span class="sxs-lookup"><span data-stu-id="f3196-116">Parent Elements</span></span>  
  
|<span data-ttu-id="f3196-117">項目</span><span class="sxs-lookup"><span data-stu-id="f3196-117">Element</span></span>|<span data-ttu-id="f3196-118">描述</span><span class="sxs-lookup"><span data-stu-id="f3196-118">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="f3196-119">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f3196-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3196-120">備註</span><span class="sxs-lookup"><span data-stu-id="f3196-120">Remarks</span></span>  
 <span data-ttu-id="f3196-121">`<system.identityModel>`將區段新增至設定檔，將服務或應用程式設定為使用 Windows Identity Foundation （WIF）。</span><span class="sxs-lookup"><span data-stu-id="f3196-121">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="f3196-122">`<system.identityModel>`元素是<xref:System.IdentityModel.Configuration.SystemIdentityModelSection>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="f3196-122">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3196-123">範例</span><span class="sxs-lookup"><span data-stu-id="f3196-123">Example</span></span>  
 <span data-ttu-id="f3196-124">下列範例顯示如何將`<system.identityModel>`區段新增至設定檔。</span><span class="sxs-lookup"><span data-stu-id="f3196-124">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="f3196-125">您必須先在`<configSections>`元素下新增設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="f3196-125">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="f3196-126">接著，您可以將`<system.IdentityModel>`元素新增至設定檔，以指定一或多個身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="f3196-126">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3196-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3196-127">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
