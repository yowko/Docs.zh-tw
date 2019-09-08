---
title: 自訂認證與認證驗證
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795813"
---
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="5723c-102">自訂認證與認證驗證</span><span class="sxs-lookup"><span data-stu-id="5723c-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="5723c-103">Windows Communication Foundation （WCF）中的安全性是以服務與用戶端之間的認證交換為基礎。</span><span class="sxs-lookup"><span data-stu-id="5723c-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="5723c-104">使用一般認證類型就可滿足大多數安全性案例，例如 Windows (Kerberos)、使用者名稱和密碼以及憑證。</span><span class="sxs-lookup"><span data-stu-id="5723c-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="5723c-105">不過，如果需要新的認證類型，可在本節的各主題中找到如何處理及驗證新類型的方法。</span><span class="sxs-lookup"><span data-stu-id="5723c-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5723c-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="5723c-106">In This Section</span></span>  
 [<span data-ttu-id="5723c-107">如何：建立採用自訂憑證驗證程式的服務</span><span class="sxs-lookup"><span data-stu-id="5723c-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="5723c-108">說明如何藉由繼承<xref:System.IdentityModel.Selectors.X509CertificateValidator>自類別來自訂 WCF 驗證。</span><span class="sxs-lookup"><span data-stu-id="5723c-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="5723c-109">逐步解說：建立自訂用戶端和服務認證</span><span class="sxs-lookup"><span data-stu-id="5723c-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="5723c-110">示範如何擴充<xref:System.ServiceModel.Description.ClientCredentials>和<xref:System.ServiceModel.Description.ServiceCredentials>類別，以容納新的認證類型。</span><span class="sxs-lookup"><span data-stu-id="5723c-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="5723c-111">而這是說明建立自訂認證類型之主題系列中的第一項。</span><span class="sxs-lookup"><span data-stu-id="5723c-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="5723c-112">如何：建立自訂安全性權杖提供者</span><span class="sxs-lookup"><span data-stu-id="5723c-112">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="5723c-113">說明如何建立安全性權杖提供者，以處理新認證類型並傳回認證的新權杖。</span><span class="sxs-lookup"><span data-stu-id="5723c-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="5723c-114">這是主題系列中的第二個主題。</span><span class="sxs-lookup"><span data-stu-id="5723c-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="5723c-115">如何：建立自訂安全性權杖驗證器</span><span class="sxs-lookup"><span data-stu-id="5723c-115">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="5723c-116">說明如何建立自訂驗證器，以驗證新認證類型。</span><span class="sxs-lookup"><span data-stu-id="5723c-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="5723c-117">這是主題系列中的第三個主題。</span><span class="sxs-lookup"><span data-stu-id="5723c-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5723c-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="5723c-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="5723c-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="5723c-119">Related Sections</span></span>  
 [<span data-ttu-id="5723c-120">驗證</span><span class="sxs-lookup"><span data-stu-id="5723c-120">Authentication</span></span>](../feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="5723c-121">同盟與發行的權杖</span><span class="sxs-lookup"><span data-stu-id="5723c-121">Federation and Issued Tokens</span></span>](../feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="5723c-122">授權</span><span class="sxs-lookup"><span data-stu-id="5723c-122">Authorization</span></span>](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="5723c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5723c-123">See also</span></span>

- [<span data-ttu-id="5723c-124">Security</span><span class="sxs-lookup"><span data-stu-id="5723c-124">Security</span></span>](../feature-details/security.md)
