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
ms.openlocfilehash: 9a2cd06c4c5a73d9fb5c4c7f09632e10c3eb0d87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991155"
---
# <a name="reliable-sessions"></a><span data-ttu-id="7e613-102">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="7e613-102">Reliable Sessions</span></span>

<span data-ttu-id="7e613-103">本章節說明哪些 Windows Communication Foundation (WCF) 可靠的工作階段、 其用途，如何以及何時要使用其中一個，哪些繫結組態支援它，而最佳做法的指標。</span><span class="sxs-lookup"><span data-stu-id="7e613-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="7e613-104">下表將針對本節重點與相關主題的詳細資料提供摘要說明。</span><span class="sxs-lookup"><span data-stu-id="7e613-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="7e613-105">可靠工作階段 WCF 提供的功能，確保端點之間傳送的訊息會透過 SOAP 或傳輸媒介傳輸和傳遞一次，並選擇性地依照傳送的順序相同。</span><span class="sxs-lookup"><span data-stu-id="7e613-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="7e613-106">若要使用的 WCF 應用程式中的可靠工作階段，請使用其中一個系統提供繫結在 WCF 中支援可靠工作階段，根據預設，或選擇，或是建立您自己自訂的繫結支援工作階段。</span><span class="sxs-lookup"><span data-stu-id="7e613-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7e613-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="7e613-107">In This Section</span></span>

<span data-ttu-id="7e613-108">[可靠工作階段概觀](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)說明可靠工作階段，使用支援可靠工作階段的不同繫結的時機，以及其運作方式。</span><span class="sxs-lookup"><span data-stu-id="7e613-108">[Reliable Sessions Overview](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="7e613-109">[如何：Exchange 訊息在可靠工作階段](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)說明如何透過使用自訂繫結組態中指定的 HTTP 建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="7e613-109">[How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="7e613-110">[如何：保護可靠工作階段內的訊息](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)說明如何保護可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="7e613-110">[How to: Secure Messages within Reliable Sessions](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="7e613-111">[如何：使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)說明如何透過 HTTPS 建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="7e613-111">[How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="7e613-112">[最佳做法的可靠工作階段](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)說明一些與使用可靠工作階段相關聯的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="7e613-112">[Best Practices for Reliable Sessions](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="7e613-113">參考資料</span><span class="sxs-lookup"><span data-stu-id="7e613-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="7e613-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e613-114">See also</span></span>

- [<span data-ttu-id="7e613-115">佇列和可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="7e613-115">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [<span data-ttu-id="7e613-116">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="7e613-116">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
