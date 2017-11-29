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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 044d67bc2b721451ade04947484899266d288d8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="673ad-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="673ad-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="673ad-103">屬性</span><span class="sxs-lookup"><span data-stu-id="673ad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="673ad-104">ID</span><span class="sxs-lookup"><span data-stu-id="673ad-104">ID</span></span>|<span data-ttu-id="673ad-105">3502</span><span class="sxs-lookup"><span data-stu-id="673ad-105">3502</span></span>|  
|<span data-ttu-id="673ad-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="673ad-106">Keywords</span></span>|<span data-ttu-id="673ad-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="673ad-107">WFServices</span></span>|  
|<span data-ttu-id="673ad-108">層級</span><span class="sxs-lookup"><span data-stu-id="673ad-108">Level</span></span>|<span data-ttu-id="673ad-109">資訊</span><span class="sxs-lookup"><span data-stu-id="673ad-109">Information</span></span>|  
|<span data-ttu-id="673ad-110">通道</span><span class="sxs-lookup"><span data-stu-id="673ad-110">Channel</span></span>|<span data-ttu-id="673ad-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="673ad-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="673ad-112">描述</span><span class="sxs-lookup"><span data-stu-id="673ad-112">Description</span></span>  
 <span data-ttu-id="673ad-113">表示已從 WorkflowService 推斷出 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="673ad-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="673ad-114">訊息</span><span class="sxs-lookup"><span data-stu-id="673ad-114">Message</span></span>  
 <span data-ttu-id="673ad-115">已從 WorkflowService 推斷出合約 '%2' 中 Name='%1' 的 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="673ad-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="673ad-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="673ad-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="673ad-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="673ad-117">Details</span></span>  
  
|<span data-ttu-id="673ad-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="673ad-118">Data Item Name</span></span>|<span data-ttu-id="673ad-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="673ad-119">Data Item Type</span></span>|<span data-ttu-id="673ad-120">描述</span><span class="sxs-lookup"><span data-stu-id="673ad-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="673ad-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="673ad-121">OperationName</span></span>|<span data-ttu-id="673ad-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="673ad-122">xs:string</span></span>|<span data-ttu-id="673ad-123">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="673ad-123">The name of the operation.</span></span>|  
|<span data-ttu-id="673ad-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="673ad-124">ContractName</span></span>|<span data-ttu-id="673ad-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="673ad-125">xs:string</span></span>|<span data-ttu-id="673ad-126">合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="673ad-126">The name of the contract.</span></span>|  
|<span data-ttu-id="673ad-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="673ad-127">IsOneWay</span></span>|<span data-ttu-id="673ad-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="673ad-128">xs:string</span></span>|<span data-ttu-id="673ad-129">True 或 False 表示合約是否為單向。</span><span class="sxs-lookup"><span data-stu-id="673ad-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="673ad-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="673ad-130">AppDomain</span></span>|<span data-ttu-id="673ad-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="673ad-131">xs:string</span></span>|<span data-ttu-id="673ad-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="673ad-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
