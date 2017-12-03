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
ms.openlocfilehash: 144ab1a4a2fd313dc7817846e3e0118145cd3f8e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="8ba83-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="8ba83-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="8ba83-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8ba83-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ba83-104">ID</span><span class="sxs-lookup"><span data-stu-id="8ba83-104">ID</span></span>|<span data-ttu-id="8ba83-105">3502</span><span class="sxs-lookup"><span data-stu-id="8ba83-105">3502</span></span>|  
|<span data-ttu-id="8ba83-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8ba83-106">Keywords</span></span>|<span data-ttu-id="8ba83-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8ba83-107">WFServices</span></span>|  
|<span data-ttu-id="8ba83-108">層級</span><span class="sxs-lookup"><span data-stu-id="8ba83-108">Level</span></span>|<span data-ttu-id="8ba83-109">資訊</span><span class="sxs-lookup"><span data-stu-id="8ba83-109">Information</span></span>|  
|<span data-ttu-id="8ba83-110">通道</span><span class="sxs-lookup"><span data-stu-id="8ba83-110">Channel</span></span>|<span data-ttu-id="8ba83-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8ba83-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8ba83-112">描述</span><span class="sxs-lookup"><span data-stu-id="8ba83-112">Description</span></span>  
 <span data-ttu-id="8ba83-113">表示已從 WorkflowService 推斷出 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="8ba83-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8ba83-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8ba83-114">Message</span></span>  
 <span data-ttu-id="8ba83-115">已從 WorkflowService 推斷出合約 '%2' 中 Name='%1' 的 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="8ba83-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="8ba83-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="8ba83-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8ba83-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8ba83-117">Details</span></span>  
  
|<span data-ttu-id="8ba83-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8ba83-118">Data Item Name</span></span>|<span data-ttu-id="8ba83-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8ba83-119">Data Item Type</span></span>|<span data-ttu-id="8ba83-120">描述</span><span class="sxs-lookup"><span data-stu-id="8ba83-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8ba83-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="8ba83-121">OperationName</span></span>|<span data-ttu-id="8ba83-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ba83-122">xs:string</span></span>|<span data-ttu-id="8ba83-123">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ba83-123">The name of the operation.</span></span>|  
|<span data-ttu-id="8ba83-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="8ba83-124">ContractName</span></span>|<span data-ttu-id="8ba83-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ba83-125">xs:string</span></span>|<span data-ttu-id="8ba83-126">合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="8ba83-126">The name of the contract.</span></span>|  
|<span data-ttu-id="8ba83-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="8ba83-127">IsOneWay</span></span>|<span data-ttu-id="8ba83-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ba83-128">xs:string</span></span>|<span data-ttu-id="8ba83-129">True 或 False 表示合約是否為單向。</span><span class="sxs-lookup"><span data-stu-id="8ba83-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="8ba83-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8ba83-130">AppDomain</span></span>|<span data-ttu-id="8ba83-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="8ba83-131">xs:string</span></span>|<span data-ttu-id="8ba83-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8ba83-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
