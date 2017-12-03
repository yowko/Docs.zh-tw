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
ms.openlocfilehash: 8ea57cc60f9626763308267a98624c825f8312b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="d1536-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="d1536-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="d1536-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d1536-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1536-104">ID</span><span class="sxs-lookup"><span data-stu-id="d1536-104">ID</span></span>|<span data-ttu-id="d1536-105">3557</span><span class="sxs-lookup"><span data-stu-id="d1536-105">3557</span></span>|  
|<span data-ttu-id="d1536-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d1536-106">Keywords</span></span>|<span data-ttu-id="d1536-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="d1536-107">WFServices</span></span>|  
|<span data-ttu-id="d1536-108">層級</span><span class="sxs-lookup"><span data-stu-id="d1536-108">Level</span></span>|<span data-ttu-id="d1536-109">資訊</span><span class="sxs-lookup"><span data-stu-id="d1536-109">Information</span></span>|  
|<span data-ttu-id="d1536-110">通道</span><span class="sxs-lookup"><span data-stu-id="d1536-110">Channel</span></span>|<span data-ttu-id="d1536-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="d1536-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d1536-112">描述</span><span class="sxs-lookup"><span data-stu-id="d1536-112">Description</span></span>  
 <span data-ttu-id="d1536-113">表示呼叫 CommittableTransaction 上的 EndCommit 擲回 TransactionException。</span><span class="sxs-lookup"><span data-stu-id="d1536-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d1536-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d1536-114">Message</span></span>  
 <span data-ttu-id="d1536-115">呼叫 ID = '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。</span><span class="sxs-lookup"><span data-stu-id="d1536-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d1536-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1536-116">Details</span></span>  
  
|<span data-ttu-id="d1536-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d1536-117">Data Item Name</span></span>|<span data-ttu-id="d1536-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d1536-118">Data Item Type</span></span>|<span data-ttu-id="d1536-119">描述</span><span class="sxs-lookup"><span data-stu-id="d1536-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d1536-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="d1536-120">TransactionId</span></span>|<span data-ttu-id="d1536-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1536-121">xs:string</span></span>|<span data-ttu-id="d1536-122">CommittableTransaction 的 ID。</span><span class="sxs-lookup"><span data-stu-id="d1536-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="d1536-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="d1536-123">Exception</span></span>|<span data-ttu-id="d1536-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1536-124">xs:string</span></span>|<span data-ttu-id="d1536-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="d1536-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="d1536-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d1536-126">AppDomain</span></span>|<span data-ttu-id="d1536-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1536-127">xs:string</span></span>|<span data-ttu-id="d1536-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d1536-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
