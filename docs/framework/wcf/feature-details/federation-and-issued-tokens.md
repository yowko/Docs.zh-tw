---
title: 聯合與發行的權杖
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: aeffc1e2a7b61dfd9406b9f06678064533ea61ec
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595501"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="9dbdf-102">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="9dbdf-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="9dbdf-103">使用 Windows Communication Foundation （WCF），您可以建立用戶端，以安全地與執行 WS-同盟和 WS-TRUST 規格的服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="9dbdf-104">這些規格使用 XML、SOAP 和 Web 服務描述語言 (WSDL)，提供跨不同信任領域的驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9dbdf-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="9dbdf-105">In This Section</span></span>  
 [<span data-ttu-id="9dbdf-106">同盟</span><span class="sxs-lookup"><span data-stu-id="9dbdf-106">Federation</span></span>](federation.md)  
 <span data-ttu-id="9dbdf-107">提供聯合的概觀。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="9dbdf-108">聯合與信任</span><span class="sxs-lookup"><span data-stu-id="9dbdf-108">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="9dbdf-109">列出建立聯合服務或用戶端時應注意的設計問題。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="9dbdf-110">如何：建立同盟用戶端</span><span class="sxs-lookup"><span data-stu-id="9dbdf-110">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="9dbdf-111">說明使用 WCF 建立同盟用戶端的基本概念。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="9dbdf-112">HOW TO：設定聯合服務的認證</span><span class="sxs-lookup"><span data-stu-id="9dbdf-112">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="9dbdf-113">說明建立聯盟服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="9dbdf-114">如何：建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9dbdf-114">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="9dbdf-115">說明如何設定使用 `WSFederationHttpBinding` 的用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="9dbdf-116">HOW TO：建立安全性權杖服務</span><span class="sxs-lookup"><span data-stu-id="9dbdf-116">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="9dbdf-117">說明建立安全性權杖服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="9dbdf-118">安全性判斷提示標記語言 (SAML) 權杖與宣告</span><span class="sxs-lookup"><span data-stu-id="9dbdf-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="9dbdf-119">說明 Security Assertions Markup Language (SAML) 權杖，這是一個可擴充，並且可讓您建立豐富之宣告類型的權杖。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="9dbdf-120">HOW TO：設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="9dbdf-120">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="9dbdf-121">說明如何建立安全性權杖的本機簽發者。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="9dbdf-122">HOW TO：在 WSFederationHttpBinding 上停用安全工作階段</span><span class="sxs-lookup"><span data-stu-id="9dbdf-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="9dbdf-123">說明如何停用 `WSFederationHttpBinding` 上的安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="9dbdf-124">在建立要求每個用戶端都使用一個工作階段的 Web 伺服陣列時，必須停用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="9dbdf-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9dbdf-125">參考</span><span class="sxs-lookup"><span data-stu-id="9dbdf-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="9dbdf-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="9dbdf-126">See also</span></span>

- [<span data-ttu-id="9dbdf-127">授權</span><span class="sxs-lookup"><span data-stu-id="9dbdf-127">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="9dbdf-128">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="9dbdf-128">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="9dbdf-129">[Windows Server AppFabric 的資訊安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9dbdf-129">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
