---
title: "異動模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c74b1826ca280ba05420449758cdbb84dac3e93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-models"></a><span data-ttu-id="392e0-102">異動模型</span><span class="sxs-lookup"><span data-stu-id="392e0-102">Transaction Models</span></span>
<span data-ttu-id="392e0-103">本主題描述異動程式設計模型與 Microsoft 提供的基礎結構元件之間的關係。</span><span class="sxs-lookup"><span data-stu-id="392e0-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="392e0-104">在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中使用交易時，了解您並非在不同的交易式模型之間做選擇，而是在整合與一致的模型之不同層中作業相當重要。</span><span class="sxs-lookup"><span data-stu-id="392e0-104">When using transactions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="392e0-105">下列幾節詳細描述三個主要的交易元件。</span><span class="sxs-lookup"><span data-stu-id="392e0-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="392e0-106">Windows Communication Foundation 交易</span><span class="sxs-lookup"><span data-stu-id="392e0-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="392e0-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的交易支援可讓您撰選交易式服務。</span><span class="sxs-lookup"><span data-stu-id="392e0-107">The transaction support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you write transactional services.</span></span> <span data-ttu-id="392e0-108">此外，透過它對 WS-AtomicTransaction (WS-AT) 通訊協定的支援，應用程式可以使交易流向使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 或協力廠商技術建立的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="392e0-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or third-party technology.</span></span>  
  
 <span data-ttu-id="392e0-109">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或應用程式中，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 交易功能提供屬性與組態，用於以宣告方式指定應建立、流動和同步化交易的方法與時間。</span><span class="sxs-lookup"><span data-stu-id="392e0-109">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="392e0-110">System.Transactions 交易</span><span class="sxs-lookup"><span data-stu-id="392e0-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="392e0-111"><xref:System.Transactions> 命名空間會提供根據 <xref:System.Transactions.Transaction> 類別的明確程式設計模型，以及使用 <xref:System.Transactions.TransactionScope> 類別的隱含程式設計模型，而其中交易會由基礎結構自動管理。</span><span class="sxs-lookup"><span data-stu-id="392e0-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="392e0-112">如何建立交易式應用程式使用這兩個模型，請參閱[撰寫異動應用程式](http://go.microsoft.com/fwlink/?LinkId=94947)。</span><span class="sxs-lookup"><span data-stu-id="392e0-112"> how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="392e0-113">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或應用程式中，<xref:System.Transactions> 提供用於在用戶端應用程式中建立交易，以及在服務中需要時與交易明確互動的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="392e0-113">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="392e0-114">MSDTC 交易</span><span class="sxs-lookup"><span data-stu-id="392e0-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="392e0-115">Microsoft Distributed Transaction Coordinator (MSDTC) 是對分散式異動提供支援的異動管理員。</span><span class="sxs-lookup"><span data-stu-id="392e0-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="392e0-116">[DTC 程式設計人員參考](http://go.microsoft.com/fwlink/?LinkId=94948)。</span><span class="sxs-lookup"><span data-stu-id="392e0-116"> the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="392e0-117">在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務或應用程式中，MSDTC 為在用戶端或服務中建立的交易協調提供基礎結構。</span><span class="sxs-lookup"><span data-stu-id="392e0-117">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
