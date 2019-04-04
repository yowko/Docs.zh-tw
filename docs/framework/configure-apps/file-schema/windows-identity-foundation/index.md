---
title: Windows Identity Foundation 組態結構描述
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 9c8009b4d95e5aa2c3d9bb8a8958040127a9e628
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441186"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="0c85c-102">Windows Identity Foundation 組態結構描述</span><span class="sxs-lookup"><span data-stu-id="0c85c-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="0c85c-103">本節中的主題提供 Windows Identity Foundation (WIF) 組態結構描述的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0c85c-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="0c85c-104">您也可以設定應用程式透過架構所公開的類別使用 WIF。</span><span class="sxs-lookup"><span data-stu-id="0c85c-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="0c85c-105">這些類別會在處理結構描述中相關項目的章節中說明。</span><span class="sxs-lookup"><span data-stu-id="0c85c-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="0c85c-106">以下顯示 WIF 組態結構描述所公開的基本 XML 標記結構描述。</span><span class="sxs-lookup"><span data-stu-id="0c85c-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="0c85c-107">已省略屬性。</span><span class="sxs-lookup"><span data-stu-id="0c85c-107">Attributes are omitted.</span></span> <span data-ttu-id="0c85c-108">醒目提示的註解表示結構描述的主要元件。</span><span class="sxs-lookup"><span data-stu-id="0c85c-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<system.identityModel>  
    <!-- Service Configuration -->  
    <identityConfiguration>  
        <caches>  
            <sessionSecurityTokenCache />  
            <tokenReplayCache />  
        </caches>  
  
        <certificateValidation>  
            <certificateValidator />   
        </certificateValidation>  
  
        <claimsAuthenticationManager />  
  
        <claimsAuthorizationManager>  
            <optionalConfigurationElement>  
        </claimsAuthorizationManager>  
  
        <claimTypeRequired>  
            <claimType />   
        </claimTypeRequired>  
  
        <tokenReplayDetection />  
  
        <!-- Security Token Handler Collection Configuration -->  
        <securityTokenHandlers>  
            <add>  
                <!-- Can take an optional configuration element which can be one of  
                     the following or a custom element -->  
                <samlSecurityTokenHandlerRequirement>  
                    <nameClaimType>  
                    <roleClaimType>   
                </samlSecurityTokenHandlerRequirement>  
  
                <sessionSecurityTokenHandlerRequirement />  
                <x509SecurityTokenHandlerRequirement />  
                <userNameSecurityTokenHandlerRequirement />  
            </add>  
            <clear />  
            <remove />  
            <securityTokenHandlerConfiguration>  
                <audienceUris>  
                    <add>  
                    <clear>  
                    <remove>  
                </audienceUris>  
  
                <caches>  
                    <sessionSecurityTokenCache />  
                    <tokenReplayCache />  
                </caches>  
  
                <certificateValidation>  
                    <certificateValidator>   
                </certificateValidation>  
  
                <issuerNameRegistry>  
                    <!-- Can take an optional configuration element which can be   
                         the <trustedIssuers> element to configure a configuration-based  
                         issuer name registry or can be a custom element -->  
                    <trustedIssuers>  
                        <add>  
                        <clear>  
                        <remove>  
                    </trustedIssuers>  
                </issuerNameRegistry>  
  
                <issuerTokenResolver />  
                <serviceTokenResolver />  
                <tokenReplayDetection />  
            </securityTokenHandlerConfiguration>  
        </securityTokenHandlers>  
    </identityConfiguration>  
</system.identityModel>  
  
<system.identityModel.services>  
    <!-- Federation Authentication Configuration -->  
    <federatedAuthentication>  
        <cookieHandler>  
            <chunkedCookieHandler />  
            <customCookieHandler />  
        </cookieHandler>  
  
        <serviceCertificate>  
            <certificateReference>  
        </serviceCertificate>  
  
        <wsFederation />  
    </federatedAuthentication>  
</system.identityModel.services>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="0c85c-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="0c85c-109">In This Section</span></span>  
 <span data-ttu-id="0c85c-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) - 提供啟用應用程式中 WIF 選項的組態。</span><span class="sxs-lookup"><span data-stu-id="0c85c-110">[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="0c85c-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) - 提供使用 WIF 之被動同盟的組態。</span><span class="sxs-lookup"><span data-stu-id="0c85c-111">[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="0c85c-112">設定工作階段驗證模組 (SAM) 和同盟驗證模組 (WSFAM)。</span><span class="sxs-lookup"><span data-stu-id="0c85c-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
