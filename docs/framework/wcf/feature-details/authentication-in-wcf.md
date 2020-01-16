---
title: WCF 的驗證
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: abe7aff025207ad8bdf8657daba3584e6a1b2e7f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964702"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="7ee45-102">WCF 的驗證</span><span class="sxs-lookup"><span data-stu-id="7ee45-102">Authentication in WCF</span></span>
<span data-ttu-id="7ee45-103">下列主題顯示 Windows Communication Foundation （WCF）中提供驗證的各種不同機制，例如 Windows 驗證、x.509 憑證，以及使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7ee45-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ee45-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="7ee45-104">In This Section</span></span>  
 [<span data-ttu-id="7ee45-105">如何：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="7ee45-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="7ee45-106">ASP.NET 功能包括成員資格及角色提供者、用來儲存驗證時比對的使用者名稱/密碼組合之資料庫，以及供授權的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="7ee45-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="7ee45-107">本主題說明 WCF 服務如何使用相同的資料庫來驗證和授權使用者。</span><span class="sxs-lookup"><span data-stu-id="7ee45-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="7ee45-108">如何：使用自訂使用者名稱與密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="7ee45-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="7ee45-109">示範如何整合自訂使用者名稱與密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="7ee45-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="7ee45-110">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="7ee45-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="7ee45-111">作為額外的保護措施，用戶端可以藉由指定預期的服務身分*識別*來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="7ee45-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="7ee45-112">若預期識別與服務傳回的識別不符，則驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="7ee45-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="7ee45-113">安全性交涉與逾時</span><span class="sxs-lookup"><span data-stu-id="7ee45-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="7ee45-114">說明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 類別中的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 屬性。</span><span class="sxs-lookup"><span data-stu-id="7ee45-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="7ee45-115">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="7ee45-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="7ee45-116">焦點放在使用 Windows 驗證時，經常遇見的問題。</span><span class="sxs-lookup"><span data-stu-id="7ee45-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7ee45-117">參考資料</span><span class="sxs-lookup"><span data-stu-id="7ee45-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="7ee45-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="7ee45-118">Related Sections</span></span>  
 [<span data-ttu-id="7ee45-119">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="7ee45-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ee45-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="7ee45-120">See also</span></span>

- [<span data-ttu-id="7ee45-121">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="7ee45-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="7ee45-122">[Windows Server App Fabric 的安全性模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7ee45-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
