---
title: <system.identityModel>
ms.date: 03/30/2017
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
author: BrucePerlerMS
ms.openlocfilehash: 286ae88946692e6894ca3c7ee9e1348415c84ade
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943591"
---
# <a name="systemidentitymodel"></a><span data-ttu-id="dce35-102">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="dce35-102">\<system.identityModel></span></span>
<span data-ttu-id="dce35-103">提供在應用程式中啟用 Windows Identity Foundation (WIF) 選項的設定。</span><span class="sxs-lookup"><span data-stu-id="dce35-103">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>  
  
 <span data-ttu-id="dce35-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="dce35-104">\<system.identityModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce35-105">語法</span><span class="sxs-lookup"><span data-stu-id="dce35-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dce35-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dce35-106">Attributes and Elements</span></span>  
 <span data-ttu-id="dce35-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dce35-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dce35-108">屬性</span><span class="sxs-lookup"><span data-stu-id="dce35-108">Attributes</span></span>  
 <span data-ttu-id="dce35-109">無</span><span class="sxs-lookup"><span data-stu-id="dce35-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dce35-110">子元素</span><span class="sxs-lookup"><span data-stu-id="dce35-110">Child Elements</span></span>  
  
|<span data-ttu-id="dce35-111">項目</span><span class="sxs-lookup"><span data-stu-id="dce35-111">Element</span></span>|<span data-ttu-id="dce35-112">描述</span><span class="sxs-lookup"><span data-stu-id="dce35-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dce35-113">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="dce35-113">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="dce35-114">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="dce35-114">Specifies service-level identity settings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dce35-115">父項目</span><span class="sxs-lookup"><span data-stu-id="dce35-115">Parent Elements</span></span>  
  
|<span data-ttu-id="dce35-116">項目</span><span class="sxs-lookup"><span data-stu-id="dce35-116">Element</span></span>|<span data-ttu-id="dce35-117">描述</span><span class="sxs-lookup"><span data-stu-id="dce35-117">Description</span></span>|  
|-------------|-----------------|  
|`<configuration>`|<span data-ttu-id="dce35-118">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="dce35-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dce35-119">備註</span><span class="sxs-lookup"><span data-stu-id="dce35-119">Remarks</span></span>  
 <span data-ttu-id="dce35-120">`<system.identityModel>`將區段新增至設定檔, 將服務或應用程式設定為使用 Windows Identity Foundation (WIF)。</span><span class="sxs-lookup"><span data-stu-id="dce35-120">Add a `<system.identityModel>` section to the configuration file to configure a service or application to use Windows Identity Foundation (WIF).</span></span> <span data-ttu-id="dce35-121">`<system.identityModel>`元素是<xref:System.IdentityModel.Configuration.SystemIdentityModelSection>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="dce35-121">The `<system.identityModel>` element is represented by the <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dce35-122">範例</span><span class="sxs-lookup"><span data-stu-id="dce35-122">Example</span></span>  
 <span data-ttu-id="dce35-123">下列範例顯示如何將`<system.identityModel>`區段新增至設定檔。</span><span class="sxs-lookup"><span data-stu-id="dce35-123">The following example shows how to add a `<system.identityModel>` section to a configuration file.</span></span> <span data-ttu-id="dce35-124">您必須先在`<configSections>`元素下新增設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="dce35-124">You must first add the configuration section and namespace declaration under the `<configSections>` element.</span></span> <span data-ttu-id="dce35-125">接著, 您可以將`<system.IdentityModel>`元素新增至設定檔, 以指定一或多個身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="dce35-125">Then you can add the `<system.IdentityModel>` element to your configuration file to specify one or more identity configurations.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dce35-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dce35-126">See also</span></span>

- <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
