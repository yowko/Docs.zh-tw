---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: b763e087d8ead2bcc0fadd1d0223ae1bd58c9fd9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511455"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="951e6-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="951e6-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="951e6-103">屬性</span><span class="sxs-lookup"><span data-stu-id="951e6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="951e6-104">ID</span><span class="sxs-lookup"><span data-stu-id="951e6-104">ID</span></span>|<span data-ttu-id="951e6-105">4207</span><span class="sxs-lookup"><span data-stu-id="951e6-105">4207</span></span>|  
|<span data-ttu-id="951e6-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="951e6-106">Keywords</span></span>|<span data-ttu-id="951e6-107">Quota、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="951e6-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="951e6-108">層級</span><span class="sxs-lookup"><span data-stu-id="951e6-108">Level</span></span>|<span data-ttu-id="951e6-109">資訊</span><span class="sxs-lookup"><span data-stu-id="951e6-109">Information</span></span>|  
|<span data-ttu-id="951e6-110">通道</span><span class="sxs-lookup"><span data-stu-id="951e6-110">Channel</span></span>|<span data-ttu-id="951e6-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="951e6-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="951e6-112">描述</span><span class="sxs-lookup"><span data-stu-id="951e6-112">Description</span></span>  
 <span data-ttu-id="951e6-113">表示 SQL 提供者要放棄重試 SQL 命令，因為已經執行了重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="951e6-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="951e6-114">訊息</span><span class="sxs-lookup"><span data-stu-id="951e6-114">Message</span></span>  
 <span data-ttu-id="951e6-115">放棄重試 SQL 命令，因為已經執行了重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="951e6-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="951e6-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="951e6-116">Details</span></span>  
  
|<span data-ttu-id="951e6-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="951e6-117">Data Item Name</span></span>|<span data-ttu-id="951e6-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="951e6-118">Data Item Type</span></span>|<span data-ttu-id="951e6-119">描述</span><span class="sxs-lookup"><span data-stu-id="951e6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="951e6-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="951e6-120">AppDomain</span></span>|<span data-ttu-id="951e6-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="951e6-121">xs:string</span></span>|<span data-ttu-id="951e6-122">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="951e6-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
