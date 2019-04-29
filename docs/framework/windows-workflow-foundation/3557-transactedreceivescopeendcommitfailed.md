---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 444fa2e51322edd793f709fd3f92c5f9fe826522
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774448"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="11699-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="11699-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>
## <a name="properties"></a><span data-ttu-id="11699-103">屬性</span><span class="sxs-lookup"><span data-stu-id="11699-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11699-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="11699-104">ID</span></span>|<span data-ttu-id="11699-105">3557</span><span class="sxs-lookup"><span data-stu-id="11699-105">3557</span></span>|  
|<span data-ttu-id="11699-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="11699-106">Keywords</span></span>|<span data-ttu-id="11699-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="11699-107">WFServices</span></span>|  
|<span data-ttu-id="11699-108">層級</span><span class="sxs-lookup"><span data-stu-id="11699-108">Level</span></span>|<span data-ttu-id="11699-109">資訊</span><span class="sxs-lookup"><span data-stu-id="11699-109">Information</span></span>|  
|<span data-ttu-id="11699-110">通道</span><span class="sxs-lookup"><span data-stu-id="11699-110">Channel</span></span>|<span data-ttu-id="11699-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="11699-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="11699-112">描述</span><span class="sxs-lookup"><span data-stu-id="11699-112">Description</span></span>  
 <span data-ttu-id="11699-113">表示呼叫 CommittableTransaction 上的 EndCommit 擲回 TransactionException。</span><span class="sxs-lookup"><span data-stu-id="11699-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="11699-114">訊息</span><span class="sxs-lookup"><span data-stu-id="11699-114">Message</span></span>  
 <span data-ttu-id="11699-115">呼叫 ID = '%1' 之 CommittableTransaction 上的 EndCommit 擲回 TransactionException，並出現下列訊息：'%2'。</span><span class="sxs-lookup"><span data-stu-id="11699-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="11699-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="11699-116">Details</span></span>  
  
|<span data-ttu-id="11699-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="11699-117">Data Item Name</span></span>|<span data-ttu-id="11699-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="11699-118">Data Item Type</span></span>|<span data-ttu-id="11699-119">描述</span><span class="sxs-lookup"><span data-stu-id="11699-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="11699-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="11699-120">TransactionId</span></span>|<span data-ttu-id="11699-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="11699-121">xs:string</span></span>|<span data-ttu-id="11699-122">CommittableTransaction 的 ID。</span><span class="sxs-lookup"><span data-stu-id="11699-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="11699-123">例外</span><span class="sxs-lookup"><span data-stu-id="11699-123">Exception</span></span>|<span data-ttu-id="11699-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="11699-124">xs:string</span></span>|<span data-ttu-id="11699-125">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="11699-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="11699-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="11699-126">AppDomain</span></span>|<span data-ttu-id="11699-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="11699-127">xs:string</span></span>|<span data-ttu-id="11699-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="11699-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
