---
title: 自訂繫結的安全性功能
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 1b12907481ccb3f3c5f4b8aaba6ede8ebfa6228a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288303"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="d1515-102">自訂繫結的安全性功能</span><span class="sxs-lookup"><span data-stu-id="d1515-102">Security Capabilities with Custom Bindings</span></span>

<span data-ttu-id="d1515-103">您可以使用一種系統提供的繫結來執行常見的安全性工作。</span><span class="sxs-lookup"><span data-stu-id="d1515-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="d1515-104">不過，如果需要更多控制，您可以依照這些主題中的說明，使用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 來建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d1515-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="d1515-105">如需自訂系結的詳細資訊，請參閱 [自訂](../extending/custom-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="d1515-105">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1515-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="d1515-106">In This Section</span></span>  

 [<span data-ttu-id="d1515-107">SecurityBindingElement 驗證模式</span><span class="sxs-lookup"><span data-stu-id="d1515-107">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="d1515-108">說明自訂繫結的可能驗證模式。</span><span class="sxs-lookup"><span data-stu-id="d1515-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="d1515-109">作法：使用 SecurityBindingElement 建立自訂繫結</span><span class="sxs-lookup"><span data-stu-id="d1515-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="d1515-110">說明建立包含安全性項目之自訂繫結的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="d1515-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="d1515-111">作法：為指定的驗證模式建立 SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1515-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="d1515-112">說明如何建立指定之驗證模式的安全性項目。</span><span class="sxs-lookup"><span data-stu-id="d1515-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="d1515-113">作法：在 WSFederationHttpBinding 上停用安全工作階段</span><span class="sxs-lookup"><span data-stu-id="d1515-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="d1515-114">說明如何在建立聯合服務時停用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="d1515-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="d1515-115">作法：啟用訊息重新執行偵測</span><span class="sxs-lookup"><span data-stu-id="d1515-115">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="d1515-116">說明如何判斷何時會發生重新執行攻擊。</span><span class="sxs-lookup"><span data-stu-id="d1515-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="d1515-117">作法：建立支援的認證</span><span class="sxs-lookup"><span data-stu-id="d1515-117">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="d1515-118">說明如何為需要認證的服務提供支援認證。</span><span class="sxs-lookup"><span data-stu-id="d1515-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="d1515-119">作法：設定簽章確認</span><span class="sxs-lookup"><span data-stu-id="d1515-119">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="d1515-120">說明在數位簽署訊息時的簽章確認步驟。</span><span class="sxs-lookup"><span data-stu-id="d1515-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="d1515-121">作法：設定最大時鐘誤差</span><span class="sxs-lookup"><span data-stu-id="d1515-121">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="d1515-122">描述如何設定服務與用戶端之間的最大允許時間差異。</span><span class="sxs-lookup"><span data-stu-id="d1515-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="d1515-123">作法：停用數位簽章加密</span><span class="sxs-lookup"><span data-stu-id="d1515-123">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="d1515-124">說明如何從停用數位簽章加密來創造效能優勢。</span><span class="sxs-lookup"><span data-stu-id="d1515-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d1515-125">參考</span><span class="sxs-lookup"><span data-stu-id="d1515-125">Reference</span></span>  

 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="d1515-126">相關章節</span><span class="sxs-lookup"><span data-stu-id="d1515-126">Related Sections</span></span>  

 [<span data-ttu-id="d1515-127">了解保護層級</span><span class="sxs-lookup"><span data-stu-id="d1515-127">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="d1515-128">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d1515-128">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="d1515-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1515-129">See also</span></span>

- [<span data-ttu-id="d1515-130">繫結和安全性</span><span class="sxs-lookup"><span data-stu-id="d1515-130">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="d1515-131">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d1515-131">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="d1515-132">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d1515-132">System-Provided Bindings</span></span>](../system-provided-bindings.md)
