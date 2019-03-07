---
title: 1004 - WorkflowInstanceAborted
ms.date: 03/30/2017
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
ms.openlocfilehash: d34f6f1ab6af8e06a0f28fb043faf9fe16a8b211
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485183"
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="57a97-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="57a97-102">1004 - WorkflowInstanceAborted</span></span>

## <a name="properties"></a><span data-ttu-id="57a97-103">屬性</span><span class="sxs-lookup"><span data-stu-id="57a97-103">Properties</span></span>

|||
|-|-|
|<span data-ttu-id="57a97-104">ID</span><span class="sxs-lookup"><span data-stu-id="57a97-104">ID</span></span>|<span data-ttu-id="57a97-105">1004</span><span class="sxs-lookup"><span data-stu-id="57a97-105">1004</span></span>|
|<span data-ttu-id="57a97-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="57a97-106">Keywords</span></span>|<span data-ttu-id="57a97-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="57a97-107">WFRuntime</span></span>|
|<span data-ttu-id="57a97-108">層級</span><span class="sxs-lookup"><span data-stu-id="57a97-108">Level</span></span>|<span data-ttu-id="57a97-109">資訊</span><span class="sxs-lookup"><span data-stu-id="57a97-109">Information</span></span>|
|<span data-ttu-id="57a97-110">通道</span><span class="sxs-lookup"><span data-stu-id="57a97-110">Channel</span></span>|<span data-ttu-id="57a97-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="57a97-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|

## <a name="description"></a><span data-ttu-id="57a97-112">描述</span><span class="sxs-lookup"><span data-stu-id="57a97-112">Description</span></span>

<span data-ttu-id="57a97-113">表示工作流程執行個體已中止的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="57a97-113">Indicates a workflow instance has aborted with an exception.</span></span>

## <a name="message"></a><span data-ttu-id="57a97-114">訊息</span><span class="sxs-lookup"><span data-stu-id="57a97-114">Message</span></span>

<span data-ttu-id="57a97-115">WorkflowInstance Id：'%1' 已中止，並發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="57a97-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>

## <a name="details"></a><span data-ttu-id="57a97-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="57a97-116">Details</span></span>

|<span data-ttu-id="57a97-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="57a97-117">Data Item Name</span></span>|<span data-ttu-id="57a97-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="57a97-118">Data Item Type</span></span>|<span data-ttu-id="57a97-119">描述</span><span class="sxs-lookup"><span data-stu-id="57a97-119">Description</span></span>|
|--------------------|--------------------|-----------------|
|<span data-ttu-id="57a97-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="57a97-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="57a97-121">工作流程的執行個體 ID。</span><span class="sxs-lookup"><span data-stu-id="57a97-121">The instance id for the workflow</span></span>|
|<span data-ttu-id="57a97-122">例外狀況</span><span class="sxs-lookup"><span data-stu-id="57a97-122">Exception</span></span>|`xs:string`|<span data-ttu-id="57a97-123">例外狀況的例外狀況詳細資料</span><span class="sxs-lookup"><span data-stu-id="57a97-123">The exception details for the exception</span></span>|
|<span data-ttu-id="57a97-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="57a97-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="57a97-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="57a97-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
