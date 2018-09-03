---
title: 異動模型
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 8731b72d0657aa420dbb020e216c3af059916ce9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43474222"
---
# <a name="transaction-models"></a><span data-ttu-id="81da4-102">異動模型</span><span class="sxs-lookup"><span data-stu-id="81da4-102">Transaction Models</span></span>
<span data-ttu-id="81da4-103">本主題描述異動程式設計模型與 Microsoft 提供的基礎結構元件之間的關係。</span><span class="sxs-lookup"><span data-stu-id="81da4-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="81da4-104">當使用交易的 Windows Communication Foundation (WCF) 中，務必了解您不是選取不同的交易式模型之間，但而不在不同層整合與一致模型的運作。</span><span class="sxs-lookup"><span data-stu-id="81da4-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="81da4-105">下列幾節詳細描述三個主要的異動元件。</span><span class="sxs-lookup"><span data-stu-id="81da4-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="81da4-106">Windows Communication Foundation 異動</span><span class="sxs-lookup"><span data-stu-id="81da4-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="81da4-107">在 WCF 中的交易支援可讓您撰寫交易式服務。</span><span class="sxs-lookup"><span data-stu-id="81da4-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="81da4-108">此外，它對 WS-AtomicTransaction (WS-AT) 通訊協定的支援，與應用程式可以使異動流向使用 WCF 或協力廠商技術建置的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="81da4-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="81da4-109">在 WCF 服務或應用程式中，WCF 交易功能會提供屬性和組態以宣告方式指定基礎結構如何及何時應該建立、 流動，並同步處理交易。</span><span class="sxs-lookup"><span data-stu-id="81da4-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="81da4-110">System.Transactions 異動</span><span class="sxs-lookup"><span data-stu-id="81da4-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="81da4-111"><xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式設計模型，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式設計模型，而其中交易會由基礎結構自動管理。</span><span class="sxs-lookup"><span data-stu-id="81da4-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="81da4-112">如需如何建立交易式應用程式使用這兩種模型的詳細資訊，請參閱[撰寫交易式應用程式](https://go.microsoft.com/fwlink/?LinkId=94947)。</span><span class="sxs-lookup"><span data-stu-id="81da4-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="81da4-113">WCF 服務或應用程式，<xref:System.Transactions>提供程式設計模型，建立用戶端應用程式內的交易和明確交易，與互動時所需，在服務中。</span><span class="sxs-lookup"><span data-stu-id="81da4-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="81da4-114">MSDTC 異動</span><span class="sxs-lookup"><span data-stu-id="81da4-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="81da4-115">Microsoft Distributed Transaction Coordinator (MSDTC) 是對分散式異動提供支援的異動管理員。</span><span class="sxs-lookup"><span data-stu-id="81da4-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="81da4-116">如需詳細資訊，請參閱 < [DTC 程式設計人員參考](https://go.microsoft.com/fwlink/?LinkId=94948)。</span><span class="sxs-lookup"><span data-stu-id="81da4-116">For more information, see the [DTC Programmer's Reference](https://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="81da4-117">在 WCF 服務或應用程式中，MSDTC 會提供用戶端或服務中建立的異動協調基礎結構。</span><span class="sxs-lookup"><span data-stu-id="81da4-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
