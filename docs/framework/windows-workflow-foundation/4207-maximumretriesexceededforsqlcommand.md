---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: f724379ef2ea23dcca7aa75caab3f10f7635e419
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251200"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="5b467-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="5b467-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>

## <a name="properties"></a><span data-ttu-id="5b467-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5b467-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b467-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="5b467-104">ID</span></span>|<span data-ttu-id="5b467-105">4207</span><span class="sxs-lookup"><span data-stu-id="5b467-105">4207</span></span>|  
|<span data-ttu-id="5b467-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5b467-106">Keywords</span></span>|<span data-ttu-id="5b467-107">Quota、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5b467-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="5b467-108">層級</span><span class="sxs-lookup"><span data-stu-id="5b467-108">Level</span></span>|<span data-ttu-id="5b467-109">資訊</span><span class="sxs-lookup"><span data-stu-id="5b467-109">Information</span></span>|  
|<span data-ttu-id="5b467-110">通路</span><span class="sxs-lookup"><span data-stu-id="5b467-110">Channel</span></span>|<span data-ttu-id="5b467-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5b467-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5b467-112">描述</span><span class="sxs-lookup"><span data-stu-id="5b467-112">Description</span></span>  

 <span data-ttu-id="5b467-113">表示 SQL 提供者要放棄重試 SQL 命令，因為已經執行了重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="5b467-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5b467-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5b467-114">Message</span></span>  

 <span data-ttu-id="5b467-115">放棄重試 SQL 命令，因為已經執行了重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="5b467-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5b467-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5b467-116">Details</span></span>  
  
|<span data-ttu-id="5b467-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5b467-117">Data Item Name</span></span>|<span data-ttu-id="5b467-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5b467-118">Data Item Type</span></span>|<span data-ttu-id="5b467-119">描述</span><span class="sxs-lookup"><span data-stu-id="5b467-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5b467-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5b467-120">AppDomain</span></span>|<span data-ttu-id="5b467-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5b467-121">xs:string</span></span>|<span data-ttu-id="5b467-122">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5b467-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
