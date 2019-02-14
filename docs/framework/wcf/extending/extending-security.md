---
title: 擴充安全性
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: 698d65d951ed7adad5aa32e874befb15a3b24d12
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261423"
---
# <a name="extending-security"></a><span data-ttu-id="0f918-102">擴充安全性</span><span class="sxs-lookup"><span data-stu-id="0f918-102">Extending Security</span></span>
<span data-ttu-id="0f918-103">若要容納新的宣告類型和自訂的權杖，您可以擴充的安全性基礎結構的 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="0f918-103">To accommodate new claim types and custom tokens, you can extend the security infrastructure of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="0f918-104">本章節中的主題會示範如何做到這點。</span><span class="sxs-lookup"><span data-stu-id="0f918-104">The topics in this section show you how this is done.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f918-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="0f918-105">In This Section</span></span>  
  
 [<span data-ttu-id="0f918-106">自訂認證與認證驗證</span><span class="sxs-lookup"><span data-stu-id="0f918-106">Custom Credential and Credential Validation</span></span>](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md)  
 <span data-ttu-id="0f918-107">說明如何在驗證自訂認證時使用身分識別模型。</span><span class="sxs-lookup"><span data-stu-id="0f918-107">Explains how the Identity Model is used when validating custom credentials.</span></span>  
  
 [<span data-ttu-id="0f918-108">自訂權杖</span><span class="sxs-lookup"><span data-stu-id="0f918-108">Custom Tokens</span></span>](../../../../docs/framework/wcf/extending/custom-tokens.md)  
 <span data-ttu-id="0f918-109">通常從安全性權杖服務 (STS) 發行的權杖是 SAML 權杖。</span><span class="sxs-lookup"><span data-stu-id="0f918-109">Issued tokens from a Security Token Service (STS) are typically SAML tokens.</span></span> <span data-ttu-id="0f918-110">本主題會說明如何建立自訂權杖類型。</span><span class="sxs-lookup"><span data-stu-id="0f918-110">This topic explains how to create a custom token type.</span></span>  
  
 [<span data-ttu-id="0f918-111">自訂授權</span><span class="sxs-lookup"><span data-stu-id="0f918-111">Custom Authorization</span></span>](../../../../docs/framework/wcf/extending/custom-authorization.md)  
 <span data-ttu-id="0f918-112">說明如何實作自訂授權。</span><span class="sxs-lookup"><span data-stu-id="0f918-112">Explains how to implement custom authorization.</span></span>  
  
 [<span data-ttu-id="0f918-113">覆寫服務的身分識別以進行驗證</span><span class="sxs-lookup"><span data-stu-id="0f918-113">Overriding the Identity of a Service for Authentication</span></span>](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md)  
 <span data-ttu-id="0f918-114">說明如何覆寫服務的身分識別來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="0f918-114">Describes how to override the identity of a service for authentication.</span></span>  
  
 [<span data-ttu-id="0f918-115">如何：建立自訂用戶端身分識別驗證器</span><span class="sxs-lookup"><span data-stu-id="0f918-115">How to: Create a Custom Client Identity Verifier</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)  
 <span data-ttu-id="0f918-116">示範如何驗證自訂端點身分識別。</span><span class="sxs-lookup"><span data-stu-id="0f918-116">Demonstrates how to validate a custom endpoint identity.</span></span>  
  
 [<span data-ttu-id="0f918-117">如何：使用個別 X.509 憑證來簽署和加密</span><span class="sxs-lookup"><span data-stu-id="0f918-117">How to: Use Separate X.509 Certificates for Signing and Encryption</span></span>](../../../../docs/framework/wcf/extending/how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 <span data-ttu-id="0f918-118">訊息通常會以單一憑證來簽署和加密。</span><span class="sxs-lookup"><span data-stu-id="0f918-118">Messages are typically signed and encrypted with a single certificate.</span></span> <span data-ttu-id="0f918-119">本主題會說明如何能在必要時使用兩份憑證。</span><span class="sxs-lookup"><span data-stu-id="0f918-119">This topic explains how two certificates can be used, when required.</span></span>  
  
 [<span data-ttu-id="0f918-120">如何：變更 X.509 憑證之私密金鑰的密碼編譯提供者</span><span class="sxs-lookup"><span data-stu-id="0f918-120">How to: Change the Cryptographic Provider for an X.509 Certificate's Private Key</span></span>](../../../../docs/framework/wcf/extending/change-cryptographic-provider-x509-certificate-private-key.md)  
 <span data-ttu-id="0f918-121">說明如何變更用來提供 X.509 憑證之私密金鑰的密碼編譯提供者，以及如何整合到 Windows Communication Foundation (WCF) 架構的提供者。</span><span class="sxs-lookup"><span data-stu-id="0f918-121">Explains how to change the cryptographic provider used to provide an X.509 certificate's private key and how to integrate the provider into the Windows Communication Foundation (WCF) framework.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0f918-122">參考資料</span><span class="sxs-lookup"><span data-stu-id="0f918-122">Reference</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a><span data-ttu-id="0f918-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="0f918-123">Related Sections</span></span>  
 [<span data-ttu-id="0f918-124">安全性</span><span class="sxs-lookup"><span data-stu-id="0f918-124">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [<span data-ttu-id="0f918-125">基本 WCF 程式設計</span><span class="sxs-lookup"><span data-stu-id="0f918-125">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f918-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f918-126">See also</span></span>
- [<span data-ttu-id="0f918-127">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="0f918-127">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
