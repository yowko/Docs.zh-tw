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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 349844edb44e547a666f10c8d210d120ebf5a39f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="9a3b1-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="9a3b1-102">4206 - UnlockInstanceException</span></span>
## <a name="properties"></a><span data-ttu-id="9a3b1-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9a3b1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a3b1-104">ID</span><span class="sxs-lookup"><span data-stu-id="9a3b1-104">ID</span></span>|<span data-ttu-id="9a3b1-105">4206</span><span class="sxs-lookup"><span data-stu-id="9a3b1-105">4206</span></span>|  
|<span data-ttu-id="9a3b1-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9a3b1-106">Keywords</span></span>|<span data-ttu-id="9a3b1-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="9a3b1-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="9a3b1-108">層級</span><span class="sxs-lookup"><span data-stu-id="9a3b1-108">Level</span></span>|<span data-ttu-id="9a3b1-109">錯誤</span><span class="sxs-lookup"><span data-stu-id="9a3b1-109">Error</span></span>|  
|<span data-ttu-id="9a3b1-110">通道</span><span class="sxs-lookup"><span data-stu-id="9a3b1-110">Channel</span></span>|<span data-ttu-id="9a3b1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9a3b1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a3b1-112">描述</span><span class="sxs-lookup"><span data-stu-id="9a3b1-112">Description</span></span>  
 <span data-ttu-id="9a3b1-113">表示在嘗試解除鎖定執行個體時，發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9a3b1-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a3b1-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9a3b1-114">Message</span></span>  
 <span data-ttu-id="9a3b1-115">嘗試解除鎖定執行個體時，發生例外狀況 %1。</span><span class="sxs-lookup"><span data-stu-id="9a3b1-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a3b1-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9a3b1-116">Details</span></span>  
  
|<span data-ttu-id="9a3b1-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9a3b1-117">Data Item Name</span></span>|<span data-ttu-id="9a3b1-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9a3b1-118">Data Item Type</span></span>|<span data-ttu-id="9a3b1-119">描述</span><span class="sxs-lookup"><span data-stu-id="9a3b1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a3b1-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="9a3b1-120">ExceptionMessage</span></span>|<span data-ttu-id="9a3b1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a3b1-121">xs:string</span></span>|<span data-ttu-id="9a3b1-122">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="9a3b1-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="9a3b1-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a3b1-123">AppDomain</span></span>|<span data-ttu-id="9a3b1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a3b1-124">xs:string</span></span>|<span data-ttu-id="9a3b1-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9a3b1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
