---
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 48182d7c5fe8f29842a17f28c0ea296f93b31089
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251252"
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="3678a-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="3678a-102">4206 - UnlockInstanceException</span></span>

## <a name="properties"></a><span data-ttu-id="3678a-103">屬性</span><span class="sxs-lookup"><span data-stu-id="3678a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3678a-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="3678a-104">ID</span></span>|<span data-ttu-id="3678a-105">4206</span><span class="sxs-lookup"><span data-stu-id="3678a-105">4206</span></span>|  
|<span data-ttu-id="3678a-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="3678a-106">Keywords</span></span>|<span data-ttu-id="3678a-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="3678a-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="3678a-108">層級</span><span class="sxs-lookup"><span data-stu-id="3678a-108">Level</span></span>|<span data-ttu-id="3678a-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="3678a-109">Error</span></span>|  
|<span data-ttu-id="3678a-110">通路</span><span class="sxs-lookup"><span data-stu-id="3678a-110">Channel</span></span>|<span data-ttu-id="3678a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3678a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3678a-112">描述</span><span class="sxs-lookup"><span data-stu-id="3678a-112">Description</span></span>  

 <span data-ttu-id="3678a-113">表示在嘗試解除鎖定執行個體時，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3678a-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3678a-114">訊息</span><span class="sxs-lookup"><span data-stu-id="3678a-114">Message</span></span>  

 <span data-ttu-id="3678a-115">嘗試解除鎖定執行個體時，發生例外狀況 %1。</span><span class="sxs-lookup"><span data-stu-id="3678a-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3678a-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3678a-116">Details</span></span>  
  
|<span data-ttu-id="3678a-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="3678a-117">Data Item Name</span></span>|<span data-ttu-id="3678a-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="3678a-118">Data Item Type</span></span>|<span data-ttu-id="3678a-119">描述</span><span class="sxs-lookup"><span data-stu-id="3678a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3678a-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="3678a-120">ExceptionMessage</span></span>|<span data-ttu-id="3678a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3678a-121">xs:string</span></span>|<span data-ttu-id="3678a-122">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="3678a-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="3678a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3678a-123">AppDomain</span></span>|<span data-ttu-id="3678a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3678a-124">xs:string</span></span>|<span data-ttu-id="3678a-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="3678a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
