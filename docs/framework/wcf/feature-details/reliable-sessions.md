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
ms.openlocfilehash: 910ad952192243c6aa8a79417ad711d8c2a4ba2e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590536"
---
# <a name="reliable-sessions"></a><span data-ttu-id="186bc-102">可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="186bc-102">Reliable Sessions</span></span>

<span data-ttu-id="186bc-103">本節說明什麼是 Windows Communication Foundation （WCF）可靠會話、用於哪些用途、使用方式和時機、哪些系結設定支援它，以及最佳做法的指標。</span><span class="sxs-lookup"><span data-stu-id="186bc-103">This section describes what a Windows Communication Foundation (WCF) reliable session is, what it's used for, how and when to use one, what binding configurations support it, and pointers on best practices.</span></span> <span data-ttu-id="186bc-104">下表將針對本節重點與相關主題的詳細資料提供摘要說明。</span><span class="sxs-lookup"><span data-stu-id="186bc-104">The following table summarizes details about the essential points and related topics in this section.</span></span>

<span data-ttu-id="186bc-105">可靠會話 WCF 提供的功能，可確保端點之間傳送的訊息會跨 SOAP 或傳輸媒介傳輸，而且只會傳遞一次，並選擇性地以其傳送的相同順序傳送。</span><span class="sxs-lookup"><span data-stu-id="186bc-105">The reliable session WCF provides features ensuring that messages sent between endpoints are transferred across SOAP or transport intermediaries and are delivered only once and, optionally, in the same order in which they were sent.</span></span>

<span data-ttu-id="186bc-106">若要使用與 WCF 應用程式的可靠會話，請在 WCF 中使用其中一個系統提供的系結，此系結預設會支援可靠會話，或做為選項，或建立您自己的自訂系結來支援會話。</span><span class="sxs-lookup"><span data-stu-id="186bc-106">To use a reliable session with a WCF application, either use one of the system-provided bindings in WCF that support a reliable session by default or as an option, or create your own custom binding that supports the session.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="186bc-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="186bc-107">In This Section</span></span>

<span data-ttu-id="186bc-108">[可靠會話總覽](reliable-sessions-overview.md)描述可靠會話、使用時機、支援可靠會話的不同系結，以及它們的工作方式。</span><span class="sxs-lookup"><span data-stu-id="186bc-108">[Reliable Sessions Overview](reliable-sessions-overview.md) Describes reliable sessions, when to use them, the different bindings that support reliable sessions, and how they work.</span></span>

<span data-ttu-id="186bc-109">[如何：在可靠的會話內交換訊息](how-to-exchange-messages-within-a-reliable-session.md)說明如何使用設定中指定的自訂系結，透過 HTTP 建立可靠會話。</span><span class="sxs-lookup"><span data-stu-id="186bc-109">[How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md) Describes how to create a reliable session over HTTP using a custom binding specified in the configuration.</span></span>

<span data-ttu-id="186bc-110">[如何：保護可靠會話內的訊息](how-to-secure-messages-within-reliable-sessions.md)說明如何保護可靠會話的安全。</span><span class="sxs-lookup"><span data-stu-id="186bc-110">[How to: Secure Messages within Reliable Sessions](how-to-secure-messages-within-reliable-sessions.md) Describes how to secure a reliable session.</span></span>

<span data-ttu-id="186bc-111">How [to：使用 HTTPS 建立自訂可靠會話](how-to-create-a-custom-reliable-session-binding-with-https.md)系結說明如何透過 HTTPS 建立可靠會話。</span><span class="sxs-lookup"><span data-stu-id="186bc-111">[How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md) Describes how to create a reliable session over HTTPS.</span></span>

<span data-ttu-id="186bc-112">[可靠會話的最佳做法](best-practices-for-reliable-sessions.md)說明一些與使用可靠會話相關聯的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="186bc-112">[Best Practices for Reliable Sessions](best-practices-for-reliable-sessions.md) Describes some of the best practices associated with using a reliable session.</span></span>

## <a name="reference"></a><span data-ttu-id="186bc-113">參考</span><span class="sxs-lookup"><span data-stu-id="186bc-113">Reference</span></span>

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a><span data-ttu-id="186bc-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="186bc-114">See also</span></span>

- [<span data-ttu-id="186bc-115">佇列和可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="186bc-115">Queues and Reliable Sessions</span></span>](queues-and-reliable-sessions.md)
- [<span data-ttu-id="186bc-116">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="186bc-116">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
