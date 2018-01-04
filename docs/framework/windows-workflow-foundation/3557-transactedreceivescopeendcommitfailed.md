---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 85e9456f6b4c1884b2e28671b304728135b6b1d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="e1c20-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="e1c20-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="e1c20-103">屬性</span><span class="sxs-lookup"><span data-stu-id="e1c20-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1c20-104">ID</span><span class="sxs-lookup"><span data-stu-id="e1c20-104">ID</span></span>|<span data-ttu-id="e1c20-105">3557</span><span class="sxs-lookup"><span data-stu-id="e1c20-105">3557</span></span>|  
|<span data-ttu-id="e1c20-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="e1c20-106">Keywords</span></span>|<span data-ttu-id="e1c20-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e1c20-107">WFServices</span></span>|  
|<span data-ttu-id="e1c20-108">層級</span><span class="sxs-lookup"><span data-stu-id="e1c20-108">Level</span></span>|<span data-ttu-id="e1c20-109">資訊</span><span class="sxs-lookup"><span data-stu-id="e1c20-109">Information</span></span>|  
|<span data-ttu-id="e1c20-110">通道</span><span class="sxs-lookup"><span data-stu-id="e1c20-110">Channel</span></span>|<span data-ttu-id="e1c20-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e1c20-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1c20-112">描述</span><span class="sxs-lookup"><span data-stu-id="e1c20-112">Description</span></span>  
 <span data-ttu-id="e1c20-113">表示呼叫 CommittableTransaction 上的 EndCommit 擲回 TransactionException。</span><span class="sxs-lookup"><span data-stu-id="e1c20-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1c20-114">訊息</span><span class="sxs-lookup"><span data-stu-id="e1c20-114">Message</span></span>  
 <span data-ttu-id="e1c20-115">呼叫 ID = '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。</span><span class="sxs-lookup"><span data-stu-id="e1c20-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1c20-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1c20-116">Details</span></span>  
  
|<span data-ttu-id="e1c20-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="e1c20-117">Data Item Name</span></span>|<span data-ttu-id="e1c20-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="e1c20-118">Data Item Type</span></span>|<span data-ttu-id="e1c20-119">描述</span><span class="sxs-lookup"><span data-stu-id="e1c20-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1c20-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="e1c20-120">TransactionId</span></span>|<span data-ttu-id="e1c20-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1c20-121">xs:string</span></span>|<span data-ttu-id="e1c20-122">CommittableTransaction 的 ID。</span><span class="sxs-lookup"><span data-stu-id="e1c20-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="e1c20-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="e1c20-123">Exception</span></span>|<span data-ttu-id="e1c20-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1c20-124">xs:string</span></span>|<span data-ttu-id="e1c20-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="e1c20-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="e1c20-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1c20-126">AppDomain</span></span>|<span data-ttu-id="e1c20-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e1c20-127">xs:string</span></span>|<span data-ttu-id="e1c20-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="e1c20-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
