---
title: 撰寫異動式應用程式
description: 在 .NET 中撰寫交易式應用程式。 分別使用明確或隱含的程式設計模型搭配 Transaction 類別或 TransactionScope 類別。
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 0235bb507d974e0bd3a7046ea213d8b78d870d59
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415767"
---
# <a name="writing-a-transactional-application"></a><span data-ttu-id="d4e1f-104">撰寫異動式應用程式</span><span class="sxs-lookup"><span data-stu-id="d4e1f-104">Writing a Transactional Application</span></span>
<span data-ttu-id="d4e1f-105">身為交易式應用程式設計人員，您可以利用 <xref:System.Transactions> 命名空間所提供的兩個程式撰寫模型 (Programming Model) 來建立交易。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-105">As a transactional application programmer, you can take advantage of the two programming models provided by the <xref:System.Transactions> namespace to create a transaction.</span></span> <span data-ttu-id="d4e1f-106">您可以使用類別來利用明確的程式設計模型 <xref:System.Transactions.Transaction> ，或透過使用類別，將交易由基礎結構自動管理的隱含程式設計模型運用 <xref:System.Transactions.TransactionScope> 。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-106">You can utilize the explicit programming model by using the <xref:System.Transactions.Transaction> class, or the implicit programming model in which transactions are automatically managed by the infrastructure, by using the <xref:System.Transactions.TransactionScope> class.</span></span> <span data-ttu-id="d4e1f-107">我們建議您將隱含的交易模型用於開發。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-107">We recommend that you use the implicit transaction model for development.</span></span> <span data-ttu-id="d4e1f-108">您可以在[使用交易範圍來執行隱含交易](implementing-an-implicit-transaction-using-transaction-scope.md)主題中找到有關如何使用交易範圍的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-108">You can find more information on how to use a transaction scope in the [Implementing an Implicit Transaction using Transaction Scope](implementing-an-implicit-transaction-using-transaction-scope.md) topic.</span></span>  
  
 <span data-ttu-id="d4e1f-109">兩種模型都支援在程式到達一致的狀態時認可交易。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-109">Both models support committing a transaction when the program reaches a consistent state.</span></span> <span data-ttu-id="d4e1f-110">一旦成功認可，就會永久地認可交易。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-110">If the commit succeeds, the transaction is durably committed.</span></span> <span data-ttu-id="d4e1f-111">如果認可失敗，就會中止交易。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-111">If the commit fails, the transaction aborts.</span></span> <span data-ttu-id="d4e1f-112">如果應用程式無法成功完成交易，就會嘗試中止並復原交易影響。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-112">If the application program cannot successfully complete the transaction, it attempts to abort and undo the transaction's effects.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4e1f-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="d4e1f-113">In This Section</span></span>  
  
### <a name="creating-a-transaction"></a><span data-ttu-id="d4e1f-114">建立交易</span><span class="sxs-lookup"><span data-stu-id="d4e1f-114">Creating a Transaction</span></span>  
 <span data-ttu-id="d4e1f-115"><xref:System.Transactions> 命名空間會提供兩種用來建立交易的模型。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-115">The <xref:System.Transactions> namespace provides two models for creating a transaction.</span></span> <span data-ttu-id="d4e1f-116">下列主題涵蓋這些模式。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-116">These models are covered in the following topics.</span></span>  
  
 [<span data-ttu-id="d4e1f-117">使用異動範圍實作隱含異動</span><span class="sxs-lookup"><span data-stu-id="d4e1f-117">Implementing an Implicit Transaction using Transaction Scope</span></span>](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 <span data-ttu-id="d4e1f-118">說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.TransactionScope> 類別來支援建立隱含的交易。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-118">Describes how the <xref:System.Transactions> namespace supports creating implicit transactions using the <xref:System.Transactions.TransactionScope> class.</span></span>  
  
 [<span data-ttu-id="d4e1f-119">使用 CommittableTransaction 實作明確異動</span><span class="sxs-lookup"><span data-stu-id="d4e1f-119">Implementing an Explicit Transaction using CommittableTransaction</span></span>](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 <span data-ttu-id="d4e1f-120">說明 <xref:System.Transactions> 命名空間如何透過 <xref:System.Transactions.CommittableTransaction> 類別來支援建立明確的交易。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-120">Describes how the <xref:System.Transactions> namespace supports creating explicit transactions using the <xref:System.Transactions.CommittableTransaction> class.</span></span>  
  
### <a name="escalating-transaction-management"></a><span data-ttu-id="d4e1f-121">擴大交易管理</span><span class="sxs-lookup"><span data-stu-id="d4e1f-121">Escalating Transaction Management</span></span>  
 <span data-ttu-id="d4e1f-122">當交易需要存取位於另一個應用程式定義域的資源時，或是當您想要登記到另一個永久性的資源管理員時，交易會自動擴大為受到 MSDTC 管理。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-122">When a transaction needs to access a resource in another application domain, or if you want to enlist in another durable resource manager, the transaction is automatically escalated to be managed by the MSDTC.</span></span> <span data-ttu-id="d4e1f-123">交易[管理擴大](transaction-management-escalation.md)主題中會涵蓋交易擴大。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-123">Transaction escalation is covered in the [Transaction Management Escalation](transaction-management-escalation.md) topic.</span></span>  
  
### <a name="concurrency"></a><span data-ttu-id="d4e1f-124">並行</span><span class="sxs-lookup"><span data-stu-id="d4e1f-124">Concurrency</span></span>  
 <span data-ttu-id="d4e1f-125">使用[DependentTransaction 管理並行](managing-concurrency-with-dependenttransaction.md)的主題會示範如何使用類別，在非同步工作之間達成平行存取 <xref:System.Transactions.DependentTransaction> 。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-125">The topic [Managing Concurrency with DependentTransaction](managing-concurrency-with-dependenttransaction.md) demonstrates how concurrency can be achieved between asynchronous tasks by using the <xref:System.Transactions.DependentTransaction> class.</span></span>  
  
### <a name="com-interop"></a><span data-ttu-id="d4e1f-126">COM+ Interop</span><span class="sxs-lookup"><span data-stu-id="d4e1f-126">COM+ Interop</span></span>  
 <span data-ttu-id="d4e1f-127">[與 Enterprise Services 和 COM + 交易的互通性](interoperability-with-enterprise-services-and-com-transactions.md)主題會說明如何讓您的分散式交易與 com + 交易進行互動。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-127">The topic [Interoperability with Enterprise Services and COM+ Transactions](interoperability-with-enterprise-services-and-com-transactions.md) illustrates how you can make your distributed transactions interact with COM+ transactions.</span></span>  
  
### <a name="diagnostics"></a><span data-ttu-id="d4e1f-128">診斷</span><span class="sxs-lookup"><span data-stu-id="d4e1f-128">Diagnostics</span></span>  
 <span data-ttu-id="d4e1f-129">[診斷追蹤](diagnostic-traces.md)會描述如何使用基礎結構所產生的追蹤程式碼， <xref:System.Transactions> 來疑難排解應用程式中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-129">[Diagnostic Traces](diagnostic-traces.md) describes how you can use the trace codes that are generated by the <xref:System.Transactions> infrastructure to troubleshoot errors in your applications.</span></span>  
  
### <a name="working-within-aspnet"></a><span data-ttu-id="d4e1f-130">使用 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d4e1f-130">Working within ASP.NET</span></span>  
 <span data-ttu-id="d4e1f-131">[ASP.NET 主題中的 Using](using-system-transactions-in-aspnet.md) system.string 一節會說明如何在 <xref:System.Transactions> ASP.NET 應用程式內成功使用。</span><span class="sxs-lookup"><span data-stu-id="d4e1f-131">The [Using System.Transactions in ASP.NET](using-system-transactions-in-aspnet.md) topic describes how you can successfully use <xref:System.Transactions> inside an ASP.NET application.</span></span>
