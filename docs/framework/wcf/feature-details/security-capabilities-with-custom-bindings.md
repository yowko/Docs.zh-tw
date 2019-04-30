---
title: 自訂繫結的安全性功能
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 25d203fa706eeb0d0ccf1eaf4367ffa5bd7b83aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990921"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="90d6f-102">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="90d6f-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="90d6f-103">您可以使用一種系統提供的繫結來執行常見的安全性工作。</span><span class="sxs-lookup"><span data-stu-id="90d6f-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="90d6f-104">不過，如果需要更多控制，您可以依照這些主題中的說明，使用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 來建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="90d6f-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="90d6f-105">如需有關自訂繫結的詳細資訊，請參閱 <<c0> [ 自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="90d6f-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90d6f-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="90d6f-106">In This Section</span></span>  
 [<span data-ttu-id="90d6f-107">SecurityBindingElement 驗證模式</span><span class="sxs-lookup"><span data-stu-id="90d6f-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="90d6f-108">說明自訂繫結的可能驗證模式。</span><span class="sxs-lookup"><span data-stu-id="90d6f-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="90d6f-109">如何：建立自訂繫結使用 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="90d6f-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="90d6f-110">說明建立包含安全性項目之自訂繫結的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="90d6f-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="90d6f-111">如何：為指定的驗證模式建立 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="90d6f-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="90d6f-112">說明如何建立指定之驗證模式的安全性項目。</span><span class="sxs-lookup"><span data-stu-id="90d6f-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="90d6f-113">如何：停用安全工作階段在 WSFederationHttpBinding 上</span><span class="sxs-lookup"><span data-stu-id="90d6f-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="90d6f-114">說明如何在建立聯合服務時停用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="90d6f-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="90d6f-115">如何：啟用訊息重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="90d6f-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="90d6f-116">說明如何判斷何時會發生重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="90d6f-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="90d6f-117">如何：建立支援認證</span><span class="sxs-lookup"><span data-stu-id="90d6f-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="90d6f-118">說明如何為需要認證的服務提供支援認證。</span><span class="sxs-lookup"><span data-stu-id="90d6f-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="90d6f-119">如何：設定簽章確認</span><span class="sxs-lookup"><span data-stu-id="90d6f-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="90d6f-120">說明在數位簽署訊息時的簽章確認步驟。</span><span class="sxs-lookup"><span data-stu-id="90d6f-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="90d6f-121">如何：設定最大時鐘誤差</span><span class="sxs-lookup"><span data-stu-id="90d6f-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="90d6f-122">描述如何設定服務與用戶端之間的最大允許時間差異。</span><span class="sxs-lookup"><span data-stu-id="90d6f-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="90d6f-123">如何：停用數位簽章加密</span><span class="sxs-lookup"><span data-stu-id="90d6f-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="90d6f-124">說明如何從停用數位簽章加密來創造效能優勢。</span><span class="sxs-lookup"><span data-stu-id="90d6f-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="90d6f-125">參考資料</span><span class="sxs-lookup"><span data-stu-id="90d6f-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="90d6f-126">\<security></span><span class="sxs-lookup"><span data-stu-id="90d6f-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="90d6f-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="90d6f-127">Related Sections</span></span>  
 [<span data-ttu-id="90d6f-128">了解保護層級</span><span class="sxs-lookup"><span data-stu-id="90d6f-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="90d6f-129">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="90d6f-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="90d6f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90d6f-130">See also</span></span>

- [<span data-ttu-id="90d6f-131">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="90d6f-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="90d6f-132">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="90d6f-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="90d6f-133">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="90d6f-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
