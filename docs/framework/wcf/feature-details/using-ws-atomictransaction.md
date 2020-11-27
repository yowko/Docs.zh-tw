---
title: 使用 WS-AtomicTransaction
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 22b84dc49ab723953ce36402ac14221f410dda11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281595"
---
# <a name="using-ws-atomictransaction"></a><span data-ttu-id="cb203-102">使用 WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="cb203-102">Using WS-AtomicTransaction</span></span>

<span data-ttu-id="cb203-103">WS-AtomicTransaction (WS-AT) 是一種互通的異動通訊協定，</span><span class="sxs-lookup"><span data-stu-id="cb203-103">WS-AtomicTransaction (WS-AT) is an interoperable transaction protocol.</span></span> <span data-ttu-id="cb203-104">可讓您使用 Web 服務訊息來流動分散式交易，並且以互通的方式在異質性交易基礎結構之間進行協調。</span><span class="sxs-lookup"><span data-stu-id="cb203-104">It enables you to flow distributed transactions by using Web service messages, and coordinate in an interoperable manner between heterogeneous transaction infrastructures.</span></span> <span data-ttu-id="cb203-105">WS-AT 使用兩階段的認可通訊協定，能夠在分散型應用程式、異動管理員和資源管理員之間促成不可部分完成的結果。</span><span class="sxs-lookup"><span data-stu-id="cb203-105">WS-AT uses the two-phase commit protocol to drive an atomic outcome between distributed applications, transaction managers, and resource managers.</span></span>  
  
 <span data-ttu-id="cb203-106">Windows Communication Foundation (WCF) 提供的「WS-AT 執行」（MSDTC）可提供內建于 Microsoft Distributed Transaction Coordinator (MSDTC) 交易管理員的通訊協定服務。</span><span class="sxs-lookup"><span data-stu-id="cb203-106">The WS-AT implementation Windows Communication Foundation (WCF) provides includes a protocol service built into the Microsoft Distributed Transaction Coordinator (MSDTC) transaction manager.</span></span> <span data-ttu-id="cb203-107">WCF 應用程式可以使用 WS-AT 將交易流動到其他應用程式，包括使用協力廠商技術建立的互通 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="cb203-107">Using WS-AT, WCF applications can flow transactions to other applications, including interoperable Web services built using third-party technology.</span></span>  
  
 <span data-ttu-id="cb203-108">當在用戶端應用程式和伺服器應用程式之間流動異動時，伺服器在用戶端所選取之端點上公開的繫結程序會判斷要使用的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cb203-108">When flowing a transaction between a client application and a server application, the transaction protocol used is determined by the binding that the server exposes on the endpoint the client selected.</span></span> <span data-ttu-id="cb203-109">某些 WCF 系統提供的系結預設會將 `OleTransactions` 通訊協定指定為交易傳播格式，而其他系結則預設為指定 ws-at。</span><span class="sxs-lookup"><span data-stu-id="cb203-109">Some WCF system-provided bindings default to specifying the `OleTransactions` protocol as the transaction propagation format, while others default to specifying WS-AT.</span></span> <span data-ttu-id="cb203-110">您也可以使用程式設計的方式來修改在特定繫結程序中選擇的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="cb203-110">You can also programmatically modify the choice of transaction protocol inside a given binding.</span></span>  
  
 <span data-ttu-id="cb203-111">選擇的通訊協定會影響：</span><span class="sxs-lookup"><span data-stu-id="cb203-111">The choice of protocol influences:</span></span>  
  
- <span data-ttu-id="cb203-112">用來將交易從用戶端流動至伺服器的訊息標頭格式。</span><span class="sxs-lookup"><span data-stu-id="cb203-112">The format of the message headers used to flow the transaction from client to server.</span></span>  
  
- <span data-ttu-id="cb203-113">用來在用戶端異動管理員和伺服器異動之間執行兩階段認可通訊協定的網路通訊協定，能夠解析異動的結果。</span><span class="sxs-lookup"><span data-stu-id="cb203-113">The network protocol used to run the two-phase commit protocol between the client's transaction manager and the server's transaction, in order to resolve the outcome of the transaction.</span></span>  
  
 <span data-ttu-id="cb203-114">如果伺服器和用戶端是使用 WCF 撰寫的，您就不需要使用 WS-AT。</span><span class="sxs-lookup"><span data-stu-id="cb203-114">If the server and client are written using WCF, you do not need to use WS-AT.</span></span> <span data-ttu-id="cb203-115">您可以改為使用已啟用 `NetTcpBinding` 屬性的 `TransactionFlow` 預設值，這樣就會使用 `OleTransactions` 通訊協定來替代。</span><span class="sxs-lookup"><span data-stu-id="cb203-115">Instead, you can use the default settings of `NetTcpBinding` with the `TransactionFlow` attribute enabled, which will use the `OleTransactions` protocol instead.</span></span> <span data-ttu-id="cb203-116">如需詳細資訊，請參閱 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="cb203-116">For more information, see [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md).</span></span> <span data-ttu-id="cb203-117">否則，如果您要流動異動至使用協力廠商技術建置的 Web 服務，就必須使用 WS-AT。</span><span class="sxs-lookup"><span data-stu-id="cb203-117">Otherwise, if you are flowing transactions to Web services built on third-party technologies, you must use WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb203-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb203-118">See also</span></span>

- [<span data-ttu-id="cb203-119">設定 WS-Atomic 交易支援</span><span class="sxs-lookup"><span data-stu-id="cb203-119">Configuring WS-Atomic Transaction Support</span></span>](configuring-ws-atomic-transaction-support.md)
