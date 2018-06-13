---
title: 異動模型
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: 9efe8c6994cc80957b707bbae0885a3c5896f70a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499020"
---
# <a name="transaction-models"></a><span data-ttu-id="94b32-102">異動模型</span><span class="sxs-lookup"><span data-stu-id="94b32-102">Transaction Models</span></span>
<span data-ttu-id="94b32-103">本主題描述異動程式設計模型與 Microsoft 提供的基礎結構元件之間的關係。</span><span class="sxs-lookup"><span data-stu-id="94b32-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="94b32-104">當使用 Windows Communication Foundation (WCF) 的交易，務必了解，您不選取不同的交易式模型之間而不在不同層整合與一致的模型上運作。</span><span class="sxs-lookup"><span data-stu-id="94b32-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="94b32-105">下列幾節詳細描述三個主要的異動元件。</span><span class="sxs-lookup"><span data-stu-id="94b32-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="94b32-106">Windows Communication Foundation 異動</span><span class="sxs-lookup"><span data-stu-id="94b32-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="94b32-107">在 WCF 中的交易支援可讓您撰寫交易式服務。</span><span class="sxs-lookup"><span data-stu-id="94b32-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="94b32-108">此外，透過它對 Ws-atomictransaction (WS-AT) 通訊協定的支援，應用程式可以使異動流向使用 WCF 或協力廠商技術建置的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="94b32-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="94b32-109">在 WCF 服務或應用程式中，WCF 交易功能提供屬性和組態，用於以宣告方式指定基礎結構如何及何時應該建立、 流動和同步化交易。</span><span class="sxs-lookup"><span data-stu-id="94b32-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="94b32-110">System.Transactions 異動</span><span class="sxs-lookup"><span data-stu-id="94b32-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="94b32-111"><xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式設計模型，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式設計模型，而其中交易會由基礎結構自動管理。</span><span class="sxs-lookup"><span data-stu-id="94b32-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="94b32-112">如需如何建立交易式應用程式使用這兩個模型的詳細資訊，請參閱[撰寫異動應用程式](http://go.microsoft.com/fwlink/?LinkId=94947)。</span><span class="sxs-lookup"><span data-stu-id="94b32-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="94b32-113">中的 WCF 服務或應用程式，<xref:System.Transactions>提供程式設計模型，以用戶端應用程式中建立交易並明確交易，需要時與互動，在服務中。</span><span class="sxs-lookup"><span data-stu-id="94b32-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="94b32-114">MSDTC 異動</span><span class="sxs-lookup"><span data-stu-id="94b32-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="94b32-115">Microsoft Distributed Transaction Coordinator (MSDTC) 是對分散式異動提供支援的異動管理員。</span><span class="sxs-lookup"><span data-stu-id="94b32-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="94b32-116">如需詳細資訊，請參閱[DTC 程式設計人員參考](http://go.microsoft.com/fwlink/?LinkId=94948)。</span><span class="sxs-lookup"><span data-stu-id="94b32-116">For more information, see the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="94b32-117">在 WCF 服務或應用程式中，MSDTC 會提供基礎結構以便建立用戶端或服務中的交易協調。</span><span class="sxs-lookup"><span data-stu-id="94b32-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
