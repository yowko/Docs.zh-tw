---
title: WCF 的驗證
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 401bd8901f4d8b9292e83d3e54d0afce30c9584f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785826"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="547d6-102">WCF 的驗證</span><span class="sxs-lookup"><span data-stu-id="547d6-102">Authentication in WCF</span></span>
<span data-ttu-id="547d6-103">下列主題顯示多個不同的機制，在 Windows Communication Foundation (WCF) 提供驗證，例如，Windows 驗證、 X.509 憑證和使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="547d6-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="547d6-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="547d6-104">In This Section</span></span>  
 [<span data-ttu-id="547d6-105">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="547d6-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="547d6-106">ASP.NET 功能包括成員資格及角色提供者、用來儲存驗證時比對的使用者名稱/密碼組合之資料庫，以及供授權的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="547d6-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="547d6-107">本主題說明如何 WCF 服務時，可以驗證和授權使用者使用相同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="547d6-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="547d6-108">如何：使用自訂使用者名稱與密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="547d6-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="547d6-109">示範如何整合自訂使用者名稱與密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="547d6-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="547d6-110">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="547d6-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="547d6-111">作為額外的保護，用戶端可以藉由指定預期驗證服務*識別*的服務。</span><span class="sxs-lookup"><span data-stu-id="547d6-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="547d6-112">若預期識別與服務傳回的識別不符，則驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="547d6-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="547d6-113">安全性交涉與逾時</span><span class="sxs-lookup"><span data-stu-id="547d6-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="547d6-114">說明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 類別中的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 屬性。</span><span class="sxs-lookup"><span data-stu-id="547d6-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="547d6-115">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="547d6-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="547d6-116">焦點放在使用 Windows 驗證時，經常遇見的問題。</span><span class="sxs-lookup"><span data-stu-id="547d6-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="547d6-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="547d6-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="547d6-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="547d6-118">Related Sections</span></span>  
 [<span data-ttu-id="547d6-119">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="547d6-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="547d6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="547d6-120">See Also</span></span>  
 [<span data-ttu-id="547d6-121">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="547d6-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="547d6-122">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="547d6-122">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
