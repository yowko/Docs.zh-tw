---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 4a4979047481687ef0d5c9d5891dec8f2826beed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263655"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="8e0bc-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="8e0bc-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>

## <a name="properties"></a><span data-ttu-id="8e0bc-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8e0bc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8e0bc-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="8e0bc-104">ID</span></span>|<span data-ttu-id="8e0bc-105">3557</span><span class="sxs-lookup"><span data-stu-id="8e0bc-105">3557</span></span>|  
|<span data-ttu-id="8e0bc-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8e0bc-106">Keywords</span></span>|<span data-ttu-id="8e0bc-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8e0bc-107">WFServices</span></span>|  
|<span data-ttu-id="8e0bc-108">層級</span><span class="sxs-lookup"><span data-stu-id="8e0bc-108">Level</span></span>|<span data-ttu-id="8e0bc-109">資訊</span><span class="sxs-lookup"><span data-stu-id="8e0bc-109">Information</span></span>|  
|<span data-ttu-id="8e0bc-110">通路</span><span class="sxs-lookup"><span data-stu-id="8e0bc-110">Channel</span></span>|<span data-ttu-id="8e0bc-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8e0bc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8e0bc-112">描述</span><span class="sxs-lookup"><span data-stu-id="8e0bc-112">Description</span></span>  

 <span data-ttu-id="8e0bc-113">表示呼叫 CommittableTransaction 上的 EndCommit 擲回 TransactionException。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8e0bc-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8e0bc-114">Message</span></span>  

 <span data-ttu-id="8e0bc-115">呼叫 ID = '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8e0bc-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8e0bc-116">Details</span></span>  
  
|<span data-ttu-id="8e0bc-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8e0bc-117">Data Item Name</span></span>|<span data-ttu-id="8e0bc-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8e0bc-118">Data Item Type</span></span>|<span data-ttu-id="8e0bc-119">描述</span><span class="sxs-lookup"><span data-stu-id="8e0bc-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8e0bc-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="8e0bc-120">TransactionId</span></span>|<span data-ttu-id="8e0bc-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e0bc-121">xs:string</span></span>|<span data-ttu-id="8e0bc-122">CommittableTransaction 的 ID。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="8e0bc-123">例外狀況</span><span class="sxs-lookup"><span data-stu-id="8e0bc-123">Exception</span></span>|<span data-ttu-id="8e0bc-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e0bc-124">xs:string</span></span>|<span data-ttu-id="8e0bc-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="8e0bc-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="8e0bc-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8e0bc-126">AppDomain</span></span>|<span data-ttu-id="8e0bc-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8e0bc-127">xs:string</span></span>|<span data-ttu-id="8e0bc-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8e0bc-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
