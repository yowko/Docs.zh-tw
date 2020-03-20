---
title: Windows Identity Foundation 組態結構描述
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 14d596ae77019932d169e1a84732fb8522bfc46c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152719"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="eb0a5-102">Windows Identity Foundation 組態結構描述</span><span class="sxs-lookup"><span data-stu-id="eb0a5-102">Windows Identity Foundation Configuration Schema</span></span>

<span data-ttu-id="eb0a5-103">本節中的主題提供 Windows Identity Foundation (WIF) 組態結構描述的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="eb0a5-104">還可以將應用程式佈建為通過框架公開的類使用 WIF。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="eb0a5-105">這些類別會在處理結構描述中相關項目的章節中說明。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="eb0a5-106">以下顯示 WIF 組態結構描述所公開的基本 XML 標記結構描述。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="eb0a5-107">已省略屬性。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-107">Attributes are omitted.</span></span> <span data-ttu-id="eb0a5-108">醒目提示的註解表示結構描述的主要元件。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<configuration>  
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
</configuration>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="eb0a5-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="eb0a5-109">In This Section</span></span>  

<span data-ttu-id="eb0a5-110">[系統.身份模型>\< ](system-identitymodel.md)提供用於在應用程式中啟用 WIF 選項的配置。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
<span data-ttu-id="eb0a5-111">[系統.身份模型.服務>\< ](system-identitymodel-services.md)使用 WIF 為被動聯合提供配置。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="eb0a5-112">設定工作階段驗證模組 (SAM) 和同盟驗證模組 (WSFAM)。</span><span class="sxs-lookup"><span data-stu-id="eb0a5-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
