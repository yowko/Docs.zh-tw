---
title: 可靠工作階段
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 1d87f6f4d94763dc8f6ac7e929c22b17940097ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735419"
---
# <a name="reliable-sessions"></a><span data-ttu-id="1f425-102">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="1f425-102">Reliable Sessions</span></span>

<span data-ttu-id="1f425-103">本章節說明哪些 Windows Communication Foundation (WCF) 可靠的工作階段、 其用途，如何以及何時要使用其中一個，哪些繫結組態支援它，而最佳做法的指標。</span><span class="sxs-lookup"><span data-stu-id="1f425-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="1f425-104">下表將針對本節重點與相關主題的詳細資料提供摘要說明。</span><span class="sxs-lookup"><span data-stu-id="1f425-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="1f425-105">可靠工作階段 WCF 提供的功能，確保端點之間傳送的訊息會透過 SOAP 或傳輸媒介傳輸和傳遞一次，並選擇性地依照傳送的順序相同。</span><span class="sxs-lookup"><span data-stu-id="1f425-105">The reliable session WCF provides featrues ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="1f425-106">若要使用的 WCF 應用程式中的可靠工作階段，請使用其中一個系統提供繫結在 WCF 中支援可靠工作階段，根據預設，或選擇，或是建立您自己自訂的繫結支援工作階段。</span><span class="sxs-lookup"><span data-stu-id="1f425-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1f425-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="1f425-107">In This Section</span></span>

<span data-ttu-id="1f425-108">[可靠工作階段概觀](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span><span class="sxs-lookup"><span data-stu-id="1f425-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) </span></span>  
<span data-ttu-id="1f425-109">說明可靠工作階段、使用時機、支援可靠工作階段的各種不同繫結，以及這些工作階段的運作方式。</span><span class="sxs-lookup"><span data-stu-id="1f425-109">Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="1f425-110">[如何：可靠工作階段內交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span><span class="sxs-lookup"><span data-stu-id="1f425-110">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) </span></span>  
<span data-ttu-id="1f425-111">說明如何使用組態中指定的自訂繫結，透過 HTTP 來建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="1f425-111">Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="1f425-112">[如何：保護可靠工作階段內的訊息](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="1f425-112">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) </span></span>  
<span data-ttu-id="1f425-113">說明如何保護可靠工作階段的安全。</span><span class="sxs-lookup"><span data-stu-id="1f425-113">Describes how to secure a reliable session.</span></span>

<span data-ttu-id="1f425-114">[如何：使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span><span class="sxs-lookup"><span data-stu-id="1f425-114">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) </span></span>  
<span data-ttu-id="1f425-115">說明如何透過 HTTPS 建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="1f425-115">Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="1f425-116">[可靠工作階段的最佳作法](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="1f425-116">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) </span></span>  
<span data-ttu-id="1f425-117">說明一些與使用可靠工作階段相關的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="1f425-117">Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="1f425-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="1f425-118">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="1f425-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f425-119">See also</span></span>

- [<span data-ttu-id="1f425-120">佇列和可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="1f425-120">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [<span data-ttu-id="1f425-121">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="1f425-121">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
