---
title: "交易處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c66e982715d0f7f97e7a4faa92c2de57f3b1471
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-processing"></a><span data-ttu-id="9d734-102">交易處理</span><span class="sxs-lookup"><span data-stu-id="9d734-102">Transaction Processing</span></span>
<span data-ttu-id="9d734-103">當您從線上書店購買一本書時，您以金錢來交易書籍 (以信用方式來支付)。</span><span class="sxs-lookup"><span data-stu-id="9d734-103">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="9d734-104">如果您的信用良好，接下來的一系列作業流程會確保您收到這本書，同時確保書店收到您支付的錢。</span><span class="sxs-lookup"><span data-stu-id="9d734-104">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="9d734-105">但是，如果在一系列交易過程中有任何一個環節出錯，整個交易就會失敗。</span><span class="sxs-lookup"><span data-stu-id="9d734-105">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="9d734-106">您將拿不到書，而書店也無法收到您支付的錢。</span><span class="sxs-lookup"><span data-stu-id="9d734-106">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="9d734-107">用於平衡並預測這項交易所有結果的技術，我們稱為交易處理。</span><span class="sxs-lookup"><span data-stu-id="9d734-107">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="9d734-108">交易可確保資料導向的資源不會一直更新，除非交易單元中的所有作業都已全部完成。</span><span class="sxs-lookup"><span data-stu-id="9d734-108">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="9d734-109">您可以將一系列相關作業整合到可能全部完成或全部失敗的單元中，藉此簡化錯誤復原程序並讓應用程式變得更可靠。</span><span class="sxs-lookup"><span data-stu-id="9d734-109">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="9d734-110">交易處理系統包含了裝載交易導向應用程式的電腦硬體與軟體用來執行業務運作所需的例行性交易。</span><span class="sxs-lookup"><span data-stu-id="9d734-110">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="9d734-111">常見範例包括用來管理銷售訂單輸入、機票預訂、薪資單、員工記錄、製造與出貨等項目的系統。</span><span class="sxs-lookup"><span data-stu-id="9d734-111">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="9d734-112">本節將提供有關交易處理的一般資訊，以及如何使用 Microsoft .NET Framework 來撰寫交易式應用程式與資源管理員的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="9d734-112">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d734-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="9d734-113">In This Section</span></span>  
 [<span data-ttu-id="9d734-114">交易基礎概念</span><span class="sxs-lookup"><span data-stu-id="9d734-114">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 <span data-ttu-id="9d734-115">簡介基礎交易處理名詞與概念。</span><span class="sxs-lookup"><span data-stu-id="9d734-115">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="9d734-116">System.Transactions 所提供的功能</span><span class="sxs-lookup"><span data-stu-id="9d734-116">Features Provided by System.Transactions</span></span>](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 <span data-ttu-id="9d734-117">討論如何使用 System.Transactions 中的各項功能來撰寫自己的交易式應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d734-117">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9d734-118">參考資料</span><span class="sxs-lookup"><span data-stu-id="9d734-118">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="9d734-119">提供可讓您的程式碼參與交易的各種類別。</span><span class="sxs-lookup"><span data-stu-id="9d734-119">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="9d734-120">這些類別支援了與多位分散的參與者、多階段告知和永久性登記進行的交易。</span><span class="sxs-lookup"><span data-stu-id="9d734-120">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
