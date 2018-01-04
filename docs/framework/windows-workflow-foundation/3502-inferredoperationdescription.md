---
title: 3502 - InferredOperationDescription
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e2c2464cd8c6f0c16946847a5503270453d5b019
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="b9047-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="b9047-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="b9047-103">屬性</span><span class="sxs-lookup"><span data-stu-id="b9047-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b9047-104">ID</span><span class="sxs-lookup"><span data-stu-id="b9047-104">ID</span></span>|<span data-ttu-id="b9047-105">3502</span><span class="sxs-lookup"><span data-stu-id="b9047-105">3502</span></span>|  
|<span data-ttu-id="b9047-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="b9047-106">Keywords</span></span>|<span data-ttu-id="b9047-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b9047-107">WFServices</span></span>|  
|<span data-ttu-id="b9047-108">層級</span><span class="sxs-lookup"><span data-stu-id="b9047-108">Level</span></span>|<span data-ttu-id="b9047-109">資訊</span><span class="sxs-lookup"><span data-stu-id="b9047-109">Information</span></span>|  
|<span data-ttu-id="b9047-110">通道</span><span class="sxs-lookup"><span data-stu-id="b9047-110">Channel</span></span>|<span data-ttu-id="b9047-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b9047-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b9047-112">描述</span><span class="sxs-lookup"><span data-stu-id="b9047-112">Description</span></span>  
 <span data-ttu-id="b9047-113">表示已從 WorkflowService 推斷出 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="b9047-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b9047-114">訊息</span><span class="sxs-lookup"><span data-stu-id="b9047-114">Message</span></span>  
 <span data-ttu-id="b9047-115">已從 WorkflowService 推斷出合約 '%2' 中 Name='%1' 的 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="b9047-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="b9047-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="b9047-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b9047-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b9047-117">Details</span></span>  
  
|<span data-ttu-id="b9047-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="b9047-118">Data Item Name</span></span>|<span data-ttu-id="b9047-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="b9047-119">Data Item Type</span></span>|<span data-ttu-id="b9047-120">描述</span><span class="sxs-lookup"><span data-stu-id="b9047-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b9047-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="b9047-121">OperationName</span></span>|<span data-ttu-id="b9047-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b9047-122">xs:string</span></span>|<span data-ttu-id="b9047-123">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="b9047-123">The name of the operation.</span></span>|  
|<span data-ttu-id="b9047-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="b9047-124">ContractName</span></span>|<span data-ttu-id="b9047-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b9047-125">xs:string</span></span>|<span data-ttu-id="b9047-126">合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="b9047-126">The name of the contract.</span></span>|  
|<span data-ttu-id="b9047-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="b9047-127">IsOneWay</span></span>|<span data-ttu-id="b9047-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b9047-128">xs:string</span></span>|<span data-ttu-id="b9047-129">True 或 False 表示合約是否為單向。</span><span class="sxs-lookup"><span data-stu-id="b9047-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="b9047-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b9047-130">AppDomain</span></span>|<span data-ttu-id="b9047-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="b9047-131">xs:string</span></span>|<span data-ttu-id="b9047-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="b9047-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
