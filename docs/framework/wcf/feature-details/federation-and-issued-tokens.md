---
title: "聯合與發行的權杖"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: aa3ed1b68cab19b0464067a2dc8f52be03279f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="21bce-102">聯合與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="21bce-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="21bce-103">有了 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]，您就可以建立與服務進行安全通訊的用戶端，其中實作了 WS-Federation 和 WS-Trust 規格。</span><span class="sxs-lookup"><span data-stu-id="21bce-103">With [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="21bce-104">這些規格使用 XML、SOAP 和 Web 服務描述語言 (WSDL)，提供跨不同信任領域的驗證和授權。</span><span class="sxs-lookup"><span data-stu-id="21bce-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="21bce-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="21bce-105">In This Section</span></span>  
 [<span data-ttu-id="21bce-106">同盟</span><span class="sxs-lookup"><span data-stu-id="21bce-106">Federation</span></span>](../../../../docs/framework/wcf/feature-details/federation.md)  
 <span data-ttu-id="21bce-107">提供聯合的概觀。</span><span class="sxs-lookup"><span data-stu-id="21bce-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="21bce-108">聯合與信任</span><span class="sxs-lookup"><span data-stu-id="21bce-108">Federation and Trust</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)  
 <span data-ttu-id="21bce-109">列出建立聯合服務或用戶端時應注意的設計問題。</span><span class="sxs-lookup"><span data-stu-id="21bce-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="21bce-110">如何： 建立聯合用戶端</span><span class="sxs-lookup"><span data-stu-id="21bce-110">How to: Create a Federated Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 <span data-ttu-id="21bce-111">說明以 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 建立聯合用戶端的基本概念。</span><span class="sxs-lookup"><span data-stu-id="21bce-111">Describes the basics of creating a federated client with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="21bce-112">如何： 設定聯合服務認證</span><span class="sxs-lookup"><span data-stu-id="21bce-112">How to: Configure Credentials on a Federation Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="21bce-113">說明建立聯盟服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="21bce-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="21bce-114">如何： 建立 WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="21bce-114">How to: Create a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="21bce-115">說明如何設定使用 `WSFederationHttpBinding` 的用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="21bce-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="21bce-116">如何： 建立安全性權杖服務</span><span class="sxs-lookup"><span data-stu-id="21bce-116">How to: Create a Security Token Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-token-service.md)  
 <span data-ttu-id="21bce-117">說明建立安全性權杖服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="21bce-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="21bce-118">安全性判斷提示標記語言 (SAML) 權杖與宣告</span><span class="sxs-lookup"><span data-stu-id="21bce-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](../../../../docs/framework/wcf/feature-details/saml-tokens-and-claims.md)  
 <span data-ttu-id="21bce-119">說明 Security Assertions Markup Language (SAML) 權杖，這是一個可擴充，並且可讓您建立豐富之宣告類型的權杖。</span><span class="sxs-lookup"><span data-stu-id="21bce-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="21bce-120">如何： 設定本機簽發者</span><span class="sxs-lookup"><span data-stu-id="21bce-120">How to: Configure a Local Issuer</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="21bce-121">說明如何建立安全性權杖的本機簽發者。</span><span class="sxs-lookup"><span data-stu-id="21bce-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="21bce-122">如何： 停用安全工作階段在 WSFederationHttpBinding 上</span><span class="sxs-lookup"><span data-stu-id="21bce-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="21bce-123">說明如何停用 `WSFederationHttpBinding` 上的安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="21bce-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="21bce-124">在建立要求每個用戶端都使用一個工作階段的 Web 伺服陣列時，必須停用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="21bce-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="21bce-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="21bce-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="21bce-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21bce-126">See Also</span></span>  
 [<span data-ttu-id="21bce-127">授權</span><span class="sxs-lookup"><span data-stu-id="21bce-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 [<span data-ttu-id="21bce-128">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="21bce-128">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 [<span data-ttu-id="21bce-129">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="21bce-129">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
