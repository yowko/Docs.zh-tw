---
title: WCF 的驗證
description: 瞭解 WCF 中提供驗證的數個機制，例如 Windows 驗證、x.509 憑證和使用者名稱和密碼。
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 414353b360992abea69d47de9efb22c3c77f4bf6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558273"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="9b815-103">WCF 的驗證</span><span class="sxs-lookup"><span data-stu-id="9b815-103">Authentication in WCF</span></span>
<span data-ttu-id="9b815-104">下列主題顯示 Windows Communication Foundation (WCF) 提供驗證的許多不同機制，例如 Windows 驗證、x.509 憑證，以及使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="9b815-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b815-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="9b815-105">In This Section</span></span>  
 [<span data-ttu-id="9b815-106">作法：使用 ASP.NET 成員資格提供者</span><span class="sxs-lookup"><span data-stu-id="9b815-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="9b815-107">ASP.NET 功能包括成員資格及角色提供者、用來儲存驗證時比對的使用者名稱/密碼組合之資料庫，以及供授權的使用者角色。</span><span class="sxs-lookup"><span data-stu-id="9b815-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="9b815-108">本主題說明 WCF 服務如何使用相同的資料庫來驗證和授權使用者。</span><span class="sxs-lookup"><span data-stu-id="9b815-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="9b815-109">作法：使用自訂使用者名稱與密碼驗證程式</span><span class="sxs-lookup"><span data-stu-id="9b815-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="9b815-110">示範如何整合自訂使用者名稱與密碼驗證程式。</span><span class="sxs-lookup"><span data-stu-id="9b815-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="9b815-111">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="9b815-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="9b815-112">用戶端可以藉由指定預期的服務身分 *識別* 來驗證服務，以提供額外的保護。</span><span class="sxs-lookup"><span data-stu-id="9b815-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="9b815-113">若預期識別與服務傳回的識別不符，則驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="9b815-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="9b815-114">安全性交涉與逾時</span><span class="sxs-lookup"><span data-stu-id="9b815-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="9b815-115">說明如何使用 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 類別中的 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b815-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="9b815-116">偵錯 Windows 驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="9b815-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="9b815-117">焦點放在使用 Windows 驗證時，經常遇見的問題。</span><span class="sxs-lookup"><span data-stu-id="9b815-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9b815-118">參考</span><span class="sxs-lookup"><span data-stu-id="9b815-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="9b815-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="9b815-119">Related Sections</span></span>  
 [<span data-ttu-id="9b815-120">常見的安全性案例</span><span class="sxs-lookup"><span data-stu-id="9b815-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b815-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b815-121">See also</span></span>

- [<span data-ttu-id="9b815-122">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="9b815-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="9b815-123">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9b815-123">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
