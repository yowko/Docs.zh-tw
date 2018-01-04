---
title: 4206 - UnlockInstanceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffe33e52a67578e42ad9d28adfa2067e8830ab73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="a221b-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="a221b-102">4206 - UnlockInstanceException</span></span>
## <a name="properties"></a><span data-ttu-id="a221b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="a221b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a221b-104">ID</span><span class="sxs-lookup"><span data-stu-id="a221b-104">ID</span></span>|<span data-ttu-id="a221b-105">4206</span><span class="sxs-lookup"><span data-stu-id="a221b-105">4206</span></span>|  
|<span data-ttu-id="a221b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a221b-106">Keywords</span></span>|<span data-ttu-id="a221b-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="a221b-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="a221b-108">層級</span><span class="sxs-lookup"><span data-stu-id="a221b-108">Level</span></span>|<span data-ttu-id="a221b-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="a221b-109">Error</span></span>|  
|<span data-ttu-id="a221b-110">通道</span><span class="sxs-lookup"><span data-stu-id="a221b-110">Channel</span></span>|<span data-ttu-id="a221b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a221b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a221b-112">描述</span><span class="sxs-lookup"><span data-stu-id="a221b-112">Description</span></span>  
 <span data-ttu-id="a221b-113">表示在嘗試解除鎖定執行個體時，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a221b-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a221b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="a221b-114">Message</span></span>  
 <span data-ttu-id="a221b-115">嘗試解除鎖定執行個體時，發生例外狀況 %1。</span><span class="sxs-lookup"><span data-stu-id="a221b-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a221b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a221b-116">Details</span></span>  
  
|<span data-ttu-id="a221b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="a221b-117">Data Item Name</span></span>|<span data-ttu-id="a221b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="a221b-118">Data Item Type</span></span>|<span data-ttu-id="a221b-119">描述</span><span class="sxs-lookup"><span data-stu-id="a221b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a221b-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="a221b-120">ExceptionMessage</span></span>|<span data-ttu-id="a221b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a221b-121">xs:string</span></span>|<span data-ttu-id="a221b-122">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="a221b-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="a221b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a221b-123">AppDomain</span></span>|<span data-ttu-id="a221b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a221b-124">xs:string</span></span>|<span data-ttu-id="a221b-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="a221b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
