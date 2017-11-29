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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1f9f1066f1948411d584a2dee1af2129aa3a103
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="0b8a4-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="0b8a4-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="0b8a4-103">屬性</span><span class="sxs-lookup"><span data-stu-id="0b8a4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b8a4-104">ID</span><span class="sxs-lookup"><span data-stu-id="0b8a4-104">ID</span></span>|<span data-ttu-id="0b8a4-105">3557</span><span class="sxs-lookup"><span data-stu-id="0b8a4-105">3557</span></span>|  
|<span data-ttu-id="0b8a4-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="0b8a4-106">Keywords</span></span>|<span data-ttu-id="0b8a4-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="0b8a4-107">WFServices</span></span>|  
|<span data-ttu-id="0b8a4-108">層級</span><span class="sxs-lookup"><span data-stu-id="0b8a4-108">Level</span></span>|<span data-ttu-id="0b8a4-109">資訊</span><span class="sxs-lookup"><span data-stu-id="0b8a4-109">Information</span></span>|  
|<span data-ttu-id="0b8a4-110">通道</span><span class="sxs-lookup"><span data-stu-id="0b8a4-110">Channel</span></span>|<span data-ttu-id="0b8a4-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0b8a4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0b8a4-112">描述</span><span class="sxs-lookup"><span data-stu-id="0b8a4-112">Description</span></span>  
 <span data-ttu-id="0b8a4-113">表示呼叫 CommittableTransaction 上的 EndCommit 擲回 TransactionException。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0b8a4-114">訊息</span><span class="sxs-lookup"><span data-stu-id="0b8a4-114">Message</span></span>  
 <span data-ttu-id="0b8a4-115">呼叫 ID = '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0b8a4-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0b8a4-116">Details</span></span>  
  
|<span data-ttu-id="0b8a4-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="0b8a4-117">Data Item Name</span></span>|<span data-ttu-id="0b8a4-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="0b8a4-118">Data Item Type</span></span>|<span data-ttu-id="0b8a4-119">描述</span><span class="sxs-lookup"><span data-stu-id="0b8a4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0b8a4-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="0b8a4-120">TransactionId</span></span>|<span data-ttu-id="0b8a4-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0b8a4-121">xs:string</span></span>|<span data-ttu-id="0b8a4-122">CommittableTransaction 的 ID。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="0b8a4-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="0b8a4-123">Exception</span></span>|<span data-ttu-id="0b8a4-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0b8a4-124">xs:string</span></span>|<span data-ttu-id="0b8a4-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="0b8a4-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="0b8a4-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0b8a4-126">AppDomain</span></span>|<span data-ttu-id="0b8a4-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="0b8a4-127">xs:string</span></span>|<span data-ttu-id="0b8a4-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="0b8a4-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
