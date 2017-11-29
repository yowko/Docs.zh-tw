---
title: 4210 - SqlExceptionCaught
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3fb3c780b80172db8770e717f517b97608fcb7c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="c30a8-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="c30a8-102">4210 - SqlExceptionCaught</span></span>
## <a name="properties"></a><span data-ttu-id="c30a8-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c30a8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c30a8-104">ID</span><span class="sxs-lookup"><span data-stu-id="c30a8-104">ID</span></span>|<span data-ttu-id="c30a8-105">4210</span><span class="sxs-lookup"><span data-stu-id="c30a8-105">4210</span></span>|  
|<span data-ttu-id="c30a8-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c30a8-106">Keywords</span></span>|<span data-ttu-id="c30a8-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c30a8-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c30a8-108">層級</span><span class="sxs-lookup"><span data-stu-id="c30a8-108">Level</span></span>|<span data-ttu-id="c30a8-109">警告</span><span class="sxs-lookup"><span data-stu-id="c30a8-109">Warning</span></span>|  
|<span data-ttu-id="c30a8-110">通道</span><span class="sxs-lookup"><span data-stu-id="c30a8-110">Channel</span></span>|<span data-ttu-id="c30a8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c30a8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c30a8-112">描述</span><span class="sxs-lookup"><span data-stu-id="c30a8-112">Description</span></span>  
 <span data-ttu-id="c30a8-113">表示已攔截到 SQL 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c30a8-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c30a8-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c30a8-114">Message</span></span>  
 <span data-ttu-id="c30a8-115">攔截到 SQL 例外狀況編號 %1 訊息 %2。</span><span class="sxs-lookup"><span data-stu-id="c30a8-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c30a8-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c30a8-116">Details</span></span>  
  
|<span data-ttu-id="c30a8-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c30a8-117">Data Item Name</span></span>|<span data-ttu-id="c30a8-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c30a8-118">Data Item Type</span></span>|<span data-ttu-id="c30a8-119">描述</span><span class="sxs-lookup"><span data-stu-id="c30a8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c30a8-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="c30a8-120">ErrorNumber</span></span>|<span data-ttu-id="c30a8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c30a8-121">xs:string</span></span>|<span data-ttu-id="c30a8-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="c30a8-122">The SQL error number.</span></span>|  
|<span data-ttu-id="c30a8-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="c30a8-123">ExceptionMessage</span></span>|<span data-ttu-id="c30a8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c30a8-124">xs:string</span></span>|<span data-ttu-id="c30a8-125">SQL 例外狀況的訊息。</span><span class="sxs-lookup"><span data-stu-id="c30a8-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="c30a8-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c30a8-126">AppDomain</span></span>|<span data-ttu-id="c30a8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c30a8-127">xs:string</span></span>|<span data-ttu-id="c30a8-128">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c30a8-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
