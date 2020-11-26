---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 05278067e3f86612ee4aafbe7d5eb66dc934cb85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242106"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="03cdc-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="03cdc-102">3502 - InferredOperationDescription</span></span>

## <a name="properties"></a><span data-ttu-id="03cdc-103">屬性</span><span class="sxs-lookup"><span data-stu-id="03cdc-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03cdc-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="03cdc-104">ID</span></span>|<span data-ttu-id="03cdc-105">3502</span><span class="sxs-lookup"><span data-stu-id="03cdc-105">3502</span></span>|  
|<span data-ttu-id="03cdc-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="03cdc-106">Keywords</span></span>|<span data-ttu-id="03cdc-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="03cdc-107">WFServices</span></span>|  
|<span data-ttu-id="03cdc-108">層級</span><span class="sxs-lookup"><span data-stu-id="03cdc-108">Level</span></span>|<span data-ttu-id="03cdc-109">資訊</span><span class="sxs-lookup"><span data-stu-id="03cdc-109">Information</span></span>|  
|<span data-ttu-id="03cdc-110">通路</span><span class="sxs-lookup"><span data-stu-id="03cdc-110">Channel</span></span>|<span data-ttu-id="03cdc-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="03cdc-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03cdc-112">描述</span><span class="sxs-lookup"><span data-stu-id="03cdc-112">Description</span></span>  

 <span data-ttu-id="03cdc-113">表示已從 WorkflowService 推斷出 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="03cdc-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03cdc-114">訊息</span><span class="sxs-lookup"><span data-stu-id="03cdc-114">Message</span></span>  

 <span data-ttu-id="03cdc-115">已從 WorkflowService 推斷出合約 '%2' 中 Name='%1' 的 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="03cdc-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="03cdc-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="03cdc-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03cdc-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="03cdc-117">Details</span></span>  
  
|<span data-ttu-id="03cdc-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="03cdc-118">Data Item Name</span></span>|<span data-ttu-id="03cdc-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="03cdc-119">Data Item Type</span></span>|<span data-ttu-id="03cdc-120">描述</span><span class="sxs-lookup"><span data-stu-id="03cdc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03cdc-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="03cdc-121">OperationName</span></span>|<span data-ttu-id="03cdc-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="03cdc-122">xs:string</span></span>|<span data-ttu-id="03cdc-123">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="03cdc-123">The name of the operation.</span></span>|  
|<span data-ttu-id="03cdc-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="03cdc-124">ContractName</span></span>|<span data-ttu-id="03cdc-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="03cdc-125">xs:string</span></span>|<span data-ttu-id="03cdc-126">合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="03cdc-126">The name of the contract.</span></span>|  
|<span data-ttu-id="03cdc-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="03cdc-127">IsOneWay</span></span>|<span data-ttu-id="03cdc-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="03cdc-128">xs:string</span></span>|<span data-ttu-id="03cdc-129">True 或 False 表示合約是否為單向。</span><span class="sxs-lookup"><span data-stu-id="03cdc-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="03cdc-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="03cdc-130">AppDomain</span></span>|<span data-ttu-id="03cdc-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="03cdc-131">xs:string</span></span>|<span data-ttu-id="03cdc-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="03cdc-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
