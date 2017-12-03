---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3bfe7547fafb17503c972646d344263117d9d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="5190c-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="5190c-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="5190c-103">屬性</span><span class="sxs-lookup"><span data-stu-id="5190c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5190c-104">ID</span><span class="sxs-lookup"><span data-stu-id="5190c-104">ID</span></span>|<span data-ttu-id="5190c-105">4208</span><span class="sxs-lookup"><span data-stu-id="5190c-105">4208</span></span>|  
|<span data-ttu-id="5190c-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="5190c-106">Keywords</span></span>|<span data-ttu-id="5190c-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5190c-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5190c-108">層級</span><span class="sxs-lookup"><span data-stu-id="5190c-108">Level</span></span>|<span data-ttu-id="5190c-109">資訊</span><span class="sxs-lookup"><span data-stu-id="5190c-109">Information</span></span>|  
|<span data-ttu-id="5190c-110">通道</span><span class="sxs-lookup"><span data-stu-id="5190c-110">Channel</span></span>|<span data-ttu-id="5190c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5190c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5190c-112">描述</span><span class="sxs-lookup"><span data-stu-id="5190c-112">Description</span></span>  
 <span data-ttu-id="5190c-113">表示 SQL 提供者正在重試 SQL 命令，因為發生 SQL 錯誤。</span><span class="sxs-lookup"><span data-stu-id="5190c-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5190c-114">訊息</span><span class="sxs-lookup"><span data-stu-id="5190c-114">Message</span></span>  
 <span data-ttu-id="5190c-115">重試 SQL 命令，因為出現 SQL 錯誤代碼 %1。</span><span class="sxs-lookup"><span data-stu-id="5190c-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5190c-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5190c-116">Details</span></span>  
  
|<span data-ttu-id="5190c-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="5190c-117">Data Item Name</span></span>|<span data-ttu-id="5190c-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="5190c-118">Data Item Type</span></span>|<span data-ttu-id="5190c-119">描述</span><span class="sxs-lookup"><span data-stu-id="5190c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5190c-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="5190c-120">ErrorNumber</span></span>|<span data-ttu-id="5190c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5190c-121">xs:string</span></span>|<span data-ttu-id="5190c-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="5190c-122">The SQL error number.</span></span>|  
|<span data-ttu-id="5190c-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5190c-123">AppDomain</span></span>|<span data-ttu-id="5190c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5190c-124">xs:string</span></span>|<span data-ttu-id="5190c-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="5190c-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
