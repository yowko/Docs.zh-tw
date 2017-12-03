---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eabc6a6915560d8c49e695d5d681f1544689cb07
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="b3e38-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="b3e38-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="b3e38-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b3e38-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b3e38-104">ID</span><span class="sxs-lookup"><span data-stu-id="b3e38-104">ID</span></span>|<span data-ttu-id="b3e38-105">3550</span><span class="sxs-lookup"><span data-stu-id="b3e38-105">3550</span></span>|  
|<span data-ttu-id="b3e38-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b3e38-106">Keywords</span></span>|<span data-ttu-id="b3e38-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b3e38-107">WFServices</span></span>|  
|<span data-ttu-id="b3e38-108">層級</span><span class="sxs-lookup"><span data-stu-id="b3e38-108">Level</span></span>|<span data-ttu-id="b3e38-109">資訊</span><span class="sxs-lookup"><span data-stu-id="b3e38-109">Information</span></span>|  
|<span data-ttu-id="b3e38-110">通道</span><span class="sxs-lookup"><span data-stu-id="b3e38-110">Channel</span></span>|<span data-ttu-id="b3e38-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b3e38-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b3e38-112">描述</span><span class="sxs-lookup"><span data-stu-id="b3e38-112">Description</span></span>  
 <span data-ttu-id="b3e38-113">表示緩衝接收已失敗。</span><span class="sxs-lookup"><span data-stu-id="b3e38-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="b3e38-114">當服務執行個體準備好處理這個特定作業時，就會再次嘗試此作業。</span><span class="sxs-lookup"><span data-stu-id="b3e38-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b3e38-115">訊息</span><span class="sxs-lookup"><span data-stu-id="b3e38-115">Message</span></span>  
 <span data-ttu-id="b3e38-116">目前無法執行作業 '%1'。</span><span class="sxs-lookup"><span data-stu-id="b3e38-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="b3e38-117">將在服務執行個體準備就緒可以處理這個特定作業時，再次嘗試。</span><span class="sxs-lookup"><span data-stu-id="b3e38-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b3e38-118">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b3e38-118">Details</span></span>  
  
|<span data-ttu-id="b3e38-119">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b3e38-119">Data Item Name</span></span>|<span data-ttu-id="b3e38-120">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b3e38-120">Data Item Type</span></span>|<span data-ttu-id="b3e38-121">描述</span><span class="sxs-lookup"><span data-stu-id="b3e38-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b3e38-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="b3e38-122">OperationName</span></span>|<span data-ttu-id="b3e38-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="b3e38-123">xs:string</span></span>|<span data-ttu-id="b3e38-124">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3e38-124">The name of the operation.</span></span>|  
|<span data-ttu-id="b3e38-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b3e38-125">AppDomain</span></span>|<span data-ttu-id="b3e38-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="b3e38-126">xs:string</span></span>|<span data-ttu-id="b3e38-127">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b3e38-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
