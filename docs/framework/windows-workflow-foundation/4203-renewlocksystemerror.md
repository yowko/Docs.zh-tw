---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 984f7ddae8797cba17753a618d0820d21bde5eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774344"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="c7901-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="c7901-102">4203 - RenewLockSystemError</span></span>
## <a name="properties"></a><span data-ttu-id="c7901-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c7901-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7901-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="c7901-104">ID</span></span>|<span data-ttu-id="c7901-105">4203</span><span class="sxs-lookup"><span data-stu-id="c7901-105">4203</span></span>|  
|<span data-ttu-id="c7901-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c7901-106">Keywords</span></span>|<span data-ttu-id="c7901-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c7901-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c7901-108">層級</span><span class="sxs-lookup"><span data-stu-id="c7901-108">Level</span></span>|<span data-ttu-id="c7901-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="c7901-109">Error</span></span>|  
|<span data-ttu-id="c7901-110">通道</span><span class="sxs-lookup"><span data-stu-id="c7901-110">Channel</span></span>|<span data-ttu-id="c7901-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c7901-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c7901-112">描述</span><span class="sxs-lookup"><span data-stu-id="c7901-112">Description</span></span>  
 <span data-ttu-id="c7901-113">表示因為已超過鎖定期限或已刪除鎖定擁有人，所以 SQL 提供者無法延長鎖定期限。</span><span class="sxs-lookup"><span data-stu-id="c7901-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="c7901-114">SqlWorkflowInstanceStore 即將中止。</span><span class="sxs-lookup"><span data-stu-id="c7901-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c7901-115">訊息</span><span class="sxs-lookup"><span data-stu-id="c7901-115">Message</span></span>  
 <span data-ttu-id="c7901-116">無法延長鎖定期限，已超過鎖定期限或已刪除鎖定擁有人。</span><span class="sxs-lookup"><span data-stu-id="c7901-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="c7901-117">正在中止 SqlWorkflowInstanceStore。</span><span class="sxs-lookup"><span data-stu-id="c7901-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c7901-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c7901-118">Details</span></span>  
  
|<span data-ttu-id="c7901-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c7901-119">Data Item Name</span></span>|<span data-ttu-id="c7901-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c7901-120">Data Item Type</span></span>|<span data-ttu-id="c7901-121">描述</span><span class="sxs-lookup"><span data-stu-id="c7901-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c7901-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c7901-122">AppDomain</span></span>|<span data-ttu-id="c7901-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="c7901-123">xs:string</span></span>|<span data-ttu-id="c7901-124">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c7901-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
