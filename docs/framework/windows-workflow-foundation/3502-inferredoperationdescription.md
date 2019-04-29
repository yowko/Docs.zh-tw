---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 752cd73066c3c15ecbb36c40c417ee84b3fcf184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756087"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="9e355-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="9e355-102">3502 - InferredOperationDescription</span></span>
## <a name="properties"></a><span data-ttu-id="9e355-103">屬性</span><span class="sxs-lookup"><span data-stu-id="9e355-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9e355-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="9e355-104">ID</span></span>|<span data-ttu-id="9e355-105">3502</span><span class="sxs-lookup"><span data-stu-id="9e355-105">3502</span></span>|  
|<span data-ttu-id="9e355-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="9e355-106">Keywords</span></span>|<span data-ttu-id="9e355-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="9e355-107">WFServices</span></span>|  
|<span data-ttu-id="9e355-108">層級</span><span class="sxs-lookup"><span data-stu-id="9e355-108">Level</span></span>|<span data-ttu-id="9e355-109">資訊</span><span class="sxs-lookup"><span data-stu-id="9e355-109">Information</span></span>|  
|<span data-ttu-id="9e355-110">通道</span><span class="sxs-lookup"><span data-stu-id="9e355-110">Channel</span></span>|<span data-ttu-id="9e355-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9e355-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9e355-112">描述</span><span class="sxs-lookup"><span data-stu-id="9e355-112">Description</span></span>  
 <span data-ttu-id="9e355-113">表示已從 WorkflowService 推斷出 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="9e355-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9e355-114">訊息</span><span class="sxs-lookup"><span data-stu-id="9e355-114">Message</span></span>  
 <span data-ttu-id="9e355-115">已從 WorkflowService 推斷出合約 '%2' 中 Name='%1' 的 OperationDescription。</span><span class="sxs-lookup"><span data-stu-id="9e355-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="9e355-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="9e355-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9e355-117">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9e355-117">Details</span></span>  
  
|<span data-ttu-id="9e355-118">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="9e355-118">Data Item Name</span></span>|<span data-ttu-id="9e355-119">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="9e355-119">Data Item Type</span></span>|<span data-ttu-id="9e355-120">描述</span><span class="sxs-lookup"><span data-stu-id="9e355-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9e355-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="9e355-121">OperationName</span></span>|<span data-ttu-id="9e355-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e355-122">xs:string</span></span>|<span data-ttu-id="9e355-123">作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e355-123">The name of the operation.</span></span>|  
|<span data-ttu-id="9e355-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="9e355-124">ContractName</span></span>|<span data-ttu-id="9e355-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e355-125">xs:string</span></span>|<span data-ttu-id="9e355-126">合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="9e355-126">The name of the contract.</span></span>|  
|<span data-ttu-id="9e355-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="9e355-127">IsOneWay</span></span>|<span data-ttu-id="9e355-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e355-128">xs:string</span></span>|<span data-ttu-id="9e355-129">True 或 False 表示合約是否為單向。</span><span class="sxs-lookup"><span data-stu-id="9e355-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="9e355-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9e355-130">AppDomain</span></span>|<span data-ttu-id="9e355-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="9e355-131">xs:string</span></span>|<span data-ttu-id="9e355-132">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="9e355-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
