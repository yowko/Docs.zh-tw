---
title: Windows Communication Foundation 交易概觀
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 63f3826215f24a4bab6d84709c2f9da6a9c8f4f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498552"
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="c3fe1-102">Windows Communication Foundation 異動概觀</span><span class="sxs-lookup"><span data-stu-id="c3fe1-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="c3fe1-103">異動提供了將一組動作或作業分組為單一個不可分割的執行單位。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="c3fe1-104">交易就是具有下列屬性的作業集合：</span><span class="sxs-lookup"><span data-stu-id="c3fe1-104">A transaction is a collection of operations with the following properties:</span></span>  
  
-   <span data-ttu-id="c3fe1-105">單元性 (Atomicity)。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-105">Atomicity.</span></span> <span data-ttu-id="c3fe1-106">這可確保在特定交易下完成的所有更新會被認可並變成永久性的，或確保所有更新會被取消並還原至先前的狀態。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="c3fe1-107">一致性 (Consistency)。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-107">Consistency.</span></span> <span data-ttu-id="c3fe1-108">這可保證在交易下完成的變更會呈現從某個一致狀態轉換至另一個狀態。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="c3fe1-109">例如，從支票帳戶轉帳到存款帳戶的交易並不會變更整個銀行帳戶內的總金額。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
-   <span data-ttu-id="c3fe1-110">隔離性。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-110">Isolation.</span></span> <span data-ttu-id="c3fe1-111">這可避免交易觀察屬於其他並行交易的未經認可變更。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="c3fe1-112">隔離性可提供抽象的並行，同時確保單一交易不會對其他交易的執行造成非預期的影響。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
-   <span data-ttu-id="c3fe1-113">持續性 (Durability)。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-113">Durability.</span></span> <span data-ttu-id="c3fe1-114">這個屬性表示在經過認可之後，對於 Managed 資源 (例如資料庫記錄) 的更新在遇到失敗時仍會持續。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="c3fe1-115">Windows Communication Foundation (WCF) 提供一組豐富的功能，可讓您在 Web 服務應用程式中建立分散式的交易。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-115">Windows Communication Foundation (WCF) provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 <span data-ttu-id="c3fe1-116">WCF 實作 Ws-atomictransaction (WS-AT) 通訊協定，可讓交易流動互通的應用程式，例如使用協力廠商技術建置的可互通 Web 服務的 WCF 應用程式的支援。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-116">WCF implements support for the WS-AtomicTransaction (WS-AT) protocol that enables WCF applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> <span data-ttu-id="c3fe1-117">WCF 同時也實作 OLE Transactions 通訊協定，可在案例中，您不需要 interop 功能來啟用交易流程支援。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-117">WCF also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="c3fe1-118">您可以使用應用程式組態檔，將繫結程序設定成啟用或停用異動流程，以及設定繫結程序上所需要的異動通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="c3fe1-119">此外，您也可以使用組態檔設定服務層級的異動逾時。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="c3fe1-120">如需詳細資訊，請參閱[啟用交易流程](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-120">For more information, see [Enabling Transaction Flow](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="c3fe1-121"><xref:System.ServiceModel> 命名空間 (Namespace) 中的交易屬性可讓您完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="c3fe1-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
-   <span data-ttu-id="c3fe1-122">使用 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性，以設定交易逾時和隔離等級的過濾。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="c3fe1-123">使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性，即可啟用交易功能並設定交易完成行為。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="c3fe1-124">使用合約方法上的 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 屬性，即可要求、允許或拒絕交易流程。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="c3fe1-125">如需詳細資訊，請參閱[ServiceModel 交易屬性](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="c3fe1-125">For more information, see [ServiceModel Transaction Attributes](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3fe1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3fe1-126">See Also</span></span>  
 [<span data-ttu-id="c3fe1-127">ServiceModel 異動屬性</span><span class="sxs-lookup"><span data-stu-id="c3fe1-127">ServiceModel Transaction Attributes</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [<span data-ttu-id="c3fe1-128">啟用異動流程</span><span class="sxs-lookup"><span data-stu-id="c3fe1-128">Enabling Transaction Flow</span></span>](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
