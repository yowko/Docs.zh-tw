---
title: 存取資源的安全性信任層級
description: 瞭解在 .NET 中存取資源的安全性信任層級。 有3個系統交易的主要信任層級。
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 64f298460bde99181ab8dc8be13ae95aaa846299
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141948"
---
# <a name="security-trust-levels-in-accessing-resources"></a><span data-ttu-id="bda35-104">存取資源的安全性信任層級</span><span class="sxs-lookup"><span data-stu-id="bda35-104">Security Trust Levels in Accessing Resources</span></span>
<span data-ttu-id="bda35-105">本主題說明如何針對 <xref:System.Transactions> 所公開的資源型別限制其存取。</span><span class="sxs-lookup"><span data-stu-id="bda35-105">This topic discusses how access is restricted on the types of resources that <xref:System.Transactions> exposes.</span></span>  
  
 <span data-ttu-id="bda35-106"><xref:System.Transactions> 主要有三種信任層級。</span><span class="sxs-lookup"><span data-stu-id="bda35-106">There are three main levels of trust for <xref:System.Transactions>.</span></span> <span data-ttu-id="bda35-107">信任層級會依據 <xref:System.Transactions> 所公開的資源型別，以及在存取這些資源時應該會用到的信任層級，來加以定義。</span><span class="sxs-lookup"><span data-stu-id="bda35-107">The trust levels are defined based on the types of resources that <xref:System.Transactions> exposes, and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="bda35-108"><xref:System.Transactions> 提供存取的資源是系統記憶體、共用的所有處理序資源，以及整個系統資源。</span><span class="sxs-lookup"><span data-stu-id="bda35-108">The resources that <xref:System.Transactions> provides access to are system memory, shared process wide resources, and system wide resources.</span></span> <span data-ttu-id="bda35-109">這些層級是：</span><span class="sxs-lookup"><span data-stu-id="bda35-109">The levels are:</span></span>  
  
- <span data-ttu-id="bda35-110">在單一應用程式域中使用交易之應用程式的**AllowPartiallyTrustedCallers** （APTCA）。</span><span class="sxs-lookup"><span data-stu-id="bda35-110">**AllowPartiallyTrustedCallers** (APTCA) for applications using transactions within a single application domain.</span></span>  
  
- <span data-ttu-id="bda35-111">**DistributedTransactionPermission** （DTP），適用于使用分散式交易的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda35-111">**DistributedTransactionPermission** (DTP) for applications using distributed transactions.</span></span>  
  
- <span data-ttu-id="bda35-112">永久性資源、組態管理應用程式，以及舊版 Interop 應用程式的完全信任。</span><span class="sxs-lookup"><span data-stu-id="bda35-112">Full trust for durable resources, configuration management applications, and legacy interop applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bda35-113">您不應該使用模擬內容來呼叫任何登記介面。</span><span class="sxs-lookup"><span data-stu-id="bda35-113">You should not call any of the enlistment interfaces with impersonated contexts.</span></span>  
  
## <a name="trust-levels"></a><span data-ttu-id="bda35-114">信任層級</span><span class="sxs-lookup"><span data-stu-id="bda35-114">Trust Levels</span></span>  
  
### <a name="aptca-partial-trust"></a><span data-ttu-id="bda35-115">APTCA (部分信任)</span><span class="sxs-lookup"><span data-stu-id="bda35-115">APTCA (Partial Trust)</span></span>  
 <span data-ttu-id="bda35-116"><xref:System.Transactions>元件可由部分信任的程式碼呼叫，因為它已經以**AllowPartiallyTrustedCallers**屬性（APTCA）標記。</span><span class="sxs-lookup"><span data-stu-id="bda35-116">The <xref:System.Transactions> assembly can be called by partially trusted code because it has been marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="bda35-117">這個屬性基本上會移除 <xref:System.Security.Permissions.SecurityAction.LinkDemand> **FullTrust**許可權集合的隱含，否則會自動放在每個型別中每個可公開存取的方法上。</span><span class="sxs-lookup"><span data-stu-id="bda35-117">This attribute essentially removes the implicit <xref:System.Security.Permissions.SecurityAction.LinkDemand> for the **FullTrust** permission set that is otherwise automatically placed on each publicly accessible method in each type.</span></span> <span data-ttu-id="bda35-118">然而，部分型別和成員仍舊需要更強勢的使用權限。</span><span class="sxs-lookup"><span data-stu-id="bda35-118">However, some types and members still require stronger permissions.</span></span>  
  
 <span data-ttu-id="bda35-119">APTCA 屬性可讓應用程式在單一應用程式定義域中以部分信任方式來使用交易。</span><span class="sxs-lookup"><span data-stu-id="bda35-119">The APTCA attribute enables applications to use transactions in partial trust within a single application domain.</span></span> <span data-ttu-id="bda35-120">這樣一來就可以使用非擴大規模的交易與變動性登記來處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="bda35-120">This enables non-escalated transactions and volatile enlistments that can be used for error handling.</span></span> <span data-ttu-id="bda35-121">交易雜湊資料表與使用該交易雜湊資料表的應用程式即是一例。</span><span class="sxs-lookup"><span data-stu-id="bda35-121">One example of this is a transacted hash table and an application that uses it.</span></span> <span data-ttu-id="bda35-122">您可以在單一交易中將資料加入雜湊資料表或從雜湊資料表移除資料。</span><span class="sxs-lookup"><span data-stu-id="bda35-122">Data can be added to and removed from the hash table under a single transaction.</span></span> <span data-ttu-id="bda35-123">如果交易稍後復原回來，則所有在該交易底下對雜湊資料表所做的變更都會復原。</span><span class="sxs-lookup"><span data-stu-id="bda35-123">If the transaction is later rolled back, all of the changes made to the hash table under that transaction can be undone.</span></span>  
  
### <a name="distributedtransactionpermission-dtp"></a><span data-ttu-id="bda35-124">DistributedTransactionPermission (DTP)</span><span class="sxs-lookup"><span data-stu-id="bda35-124">DistributedTransactionPermission (DTP)</span></span>  
 <span data-ttu-id="bda35-125">當 <xref:System.Transactions> 交易的規模擴大至需由 MSDTC 管理時，<xref:System.Transactions> 就會要求 <xref:System.Transactions.DistributedTransactionPermission> (DTP) 建立分散式交易。</span><span class="sxs-lookup"><span data-stu-id="bda35-125">When a <xref:System.Transactions> transaction is escalated to be managed by MSDTC, <xref:System.Transactions> demands the <xref:System.Transactions.DistributedTransactionPermission> (DTP) to create the distributed transaction.</span></span> <span data-ttu-id="bda35-126">也就是說，導致交易規模擴大的程式碼 (例如透過序列化或額外的永久性登記作業) 需要被授予 DTP。</span><span class="sxs-lookup"><span data-stu-id="bda35-126">This means that the code that causes the transaction to be escalated (such as through serialization or additional durable enlistments) would need to be granted DTP.</span></span> <span data-ttu-id="bda35-127">原先建立 <xref:System.Transactions> 交易的程式碼，不一定需要擁有此使用權限。</span><span class="sxs-lookup"><span data-stu-id="bda35-127">The code that originally created the <xref:System.Transactions> transaction does not necessarily need to possess this permission.</span></span>  
  
### <a name="fulltrust-link-demands"></a><span data-ttu-id="bda35-128">FullTrust 連結要求</span><span class="sxs-lookup"><span data-stu-id="bda35-128">FullTrust Link Demands</span></span>  
 <span data-ttu-id="bda35-129">這項權限等級主要是用來限制寫入永久性資源的應用程式權限。</span><span class="sxs-lookup"><span data-stu-id="bda35-129">This permission level is intended to restrict applications that are writing to durable resources.</span></span> <span data-ttu-id="bda35-130">一旦發生失敗，應用程式需要能夠透過交易管理員來復原，以決定交易的最後結果，方便它更新永久資料。</span><span class="sxs-lookup"><span data-stu-id="bda35-130">Upon failure, the application needs to be able to recover with the transaction manager to determine the final outcome of the transaction, so that it can update permanent data.</span></span> <span data-ttu-id="bda35-131">此類型的應用程式我們稱為永久性資源管理員。</span><span class="sxs-lookup"><span data-stu-id="bda35-131">This type of application is known as a durable source manager.</span></span> <span data-ttu-id="bda35-132">SQL 即是典型的這類應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="bda35-132">A classic example of this type of application is SQL.</span></span>  
  
 <span data-ttu-id="bda35-133">為了啟用復原，此類型的應用程式必須具備永久取用系統資源的能力。</span><span class="sxs-lookup"><span data-stu-id="bda35-133">To enable recovery, this type of application has the ability to permanently consume system resources.</span></span> <span data-ttu-id="bda35-134">這是因為可復原的交易管理員必須一直記住已經認可的交易，直到它確認所有參與交易的永久性資源管理員都已收到結果告知。</span><span class="sxs-lookup"><span data-stu-id="bda35-134">This is because the recoverable transaction manager must remember transactions that have committed until it can confirm that all durable resource managers that are participating in the transaction have received the outcome.</span></span> <span data-ttu-id="bda35-135">因此，這類型的應用程式需要完全信任，而且不應該在未獲得此信任等級之前貿然執行。</span><span class="sxs-lookup"><span data-stu-id="bda35-135">Therefore, this type of application requires full trust and should not be run unless that level of trust has been granted.</span></span>  
  
 <span data-ttu-id="bda35-136">如需永久性登記和復原的詳細資訊，請參閱將[資源登記為交易中的參與者](enlisting-resources-as-participants-in-a-transaction.md)和[執行](performing-recovery.md)復原主題。</span><span class="sxs-lookup"><span data-stu-id="bda35-136">For more information on durable enlistments and recovery, see the [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) and [Performing Recovery](performing-recovery.md) topics.</span></span>  
  
 <span data-ttu-id="bda35-137">要擁有完全信任，必須同時具備使用 COM+ 來執行舊版 Interop 工作的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bda35-137">Applications that perform legacy interop work with COM+ are also required to have full trust.</span></span>  
  
 <span data-ttu-id="bda35-138">以下是部分信任程式碼無法呼叫的類型和成員清單，因為它們是以**FullTrust**宣告式安全性屬性裝飾：</span><span class="sxs-lookup"><span data-stu-id="bda35-138">The following is a list of types and members that are not callable by partially trusted code because they are decorated with the **FullTrust** declarative security attribute:</span></span>  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 <span data-ttu-id="bda35-139">只有立即呼叫端才需要擁有**FullTrust**許可權集合，才能使用上述類型或方法。</span><span class="sxs-lookup"><span data-stu-id="bda35-139">Only the immediate caller is required to possess the **FullTrust** permission set to use the above types or methods.</span></span>
