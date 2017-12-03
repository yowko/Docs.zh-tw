---
title: "WCF 的驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9a08627e213196c2d5fb296f458a5d3a8c7bb1a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="bd30f-102">WCF 的驗證</span><span class="sxs-lookup"><span data-stu-id="bd30f-102">Authentication in WCF</span></span>
<span data-ttu-id="bd30f-103">下列主題說明 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中提供驗證的各種不同機制，例如，Windows 驗證、X.509 憑證以及使用者名稱與密碼。</span><span class="sxs-lookup"><span data-stu-id="bd30f-103">The following topics show a number of different mechanisms in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd30f-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="bd30f-104">In This Section</span></span>  
 [<span data-ttu-id="bd30f-105">如何： 使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="bd30f-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="bd30f-106">ASP.NET 功能包括成員資格及角色提供者、用來儲存驗證時比對的使用者名稱/密碼組合之資料庫，以及供授權的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="bd30f-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="bd30f-107">這個主題會說明 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務如何能使用相同的資料庫對使用者驗證與授權。</span><span class="sxs-lookup"><span data-stu-id="bd30f-107">This topic explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="bd30f-108">如何： 使用自訂的使用者名稱和密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="bd30f-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="bd30f-109">示範如何整合自訂使用者名稱與密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="bd30f-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="bd30f-110">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="bd30f-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="bd30f-111">作為額外的保護，用戶端可以藉由指定預期的驗證服務*識別*的服務。</span><span class="sxs-lookup"><span data-stu-id="bd30f-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="bd30f-112">若預期識別與服務傳回的識別不符，則驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="bd30f-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="bd30f-113">安全性交涉與逾時</span><span class="sxs-lookup"><span data-stu-id="bd30f-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="bd30f-114">說明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 類別中的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 屬性。</span><span class="sxs-lookup"><span data-stu-id="bd30f-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="bd30f-115">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="bd30f-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="bd30f-116">焦點放在使用 Windows 驗證時，經常遇見的問題。</span><span class="sxs-lookup"><span data-stu-id="bd30f-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bd30f-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="bd30f-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="bd30f-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="bd30f-118">Related Sections</span></span>  
 [<span data-ttu-id="bd30f-119">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="bd30f-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="bd30f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd30f-120">See Also</span></span>  
 [<span data-ttu-id="bd30f-121">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="bd30f-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="bd30f-122">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="bd30f-122">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
