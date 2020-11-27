---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 9249bdd0fe996ee7c1b04783ac8fef2c48063cc0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294153"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="51451-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="51451-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="51451-103">屬性</span><span class="sxs-lookup"><span data-stu-id="51451-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="51451-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="51451-104">ID</span></span>|<span data-ttu-id="51451-105">1132</span><span class="sxs-lookup"><span data-stu-id="51451-105">1132</span></span>|  
|<span data-ttu-id="51451-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="51451-106">Keywords</span></span>|<span data-ttu-id="51451-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="51451-107">WFRuntime</span></span>|  
|<span data-ttu-id="51451-108">層級</span><span class="sxs-lookup"><span data-stu-id="51451-108">Level</span></span>|<span data-ttu-id="51451-109">資訊</span><span class="sxs-lookup"><span data-stu-id="51451-109">Information</span></span>|  
|<span data-ttu-id="51451-110">通路</span><span class="sxs-lookup"><span data-stu-id="51451-110">Channel</span></span>|<span data-ttu-id="51451-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="51451-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="51451-112">描述</span><span class="sxs-lookup"><span data-stu-id="51451-112">Description</span></span>  

 <span data-ttu-id="51451-113">在 CacheMetadata 步驟期間，InvokeMethod 活動表示其於叫用方法時，未使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="51451-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="51451-114">訊息</span><span class="sxs-lookup"><span data-stu-id="51451-114">Message</span></span>  

 <span data-ttu-id="51451-115">InvokeMethod '%1' - 方法未使用非同步模式。</span><span class="sxs-lookup"><span data-stu-id="51451-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="51451-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="51451-116">Details</span></span>  
  
|<span data-ttu-id="51451-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="51451-117">Data Item Name</span></span>|<span data-ttu-id="51451-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="51451-118">Data Item Type</span></span>|<span data-ttu-id="51451-119">描述</span><span class="sxs-lookup"><span data-stu-id="51451-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="51451-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="51451-120">InvokeMethod</span></span>|<span data-ttu-id="51451-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="51451-121">xs:string</span></span>|<span data-ttu-id="51451-122">InvokeMethod 活動的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="51451-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="51451-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="51451-123">AppDomain</span></span>|<span data-ttu-id="51451-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="51451-124">xs:string</span></span>|<span data-ttu-id="51451-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="51451-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
