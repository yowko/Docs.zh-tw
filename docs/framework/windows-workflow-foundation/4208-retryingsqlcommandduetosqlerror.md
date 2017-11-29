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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01db76802b96bd32e8a01cf86b1e682defe97a06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="c6b6e-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="c6b6e-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="c6b6e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="c6b6e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c6b6e-104">ID</span><span class="sxs-lookup"><span data-stu-id="c6b6e-104">ID</span></span>|<span data-ttu-id="c6b6e-105">4208</span><span class="sxs-lookup"><span data-stu-id="c6b6e-105">4208</span></span>|  
|<span data-ttu-id="c6b6e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="c6b6e-106">Keywords</span></span>|<span data-ttu-id="c6b6e-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c6b6e-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="c6b6e-108">層級</span><span class="sxs-lookup"><span data-stu-id="c6b6e-108">Level</span></span>|<span data-ttu-id="c6b6e-109">資訊</span><span class="sxs-lookup"><span data-stu-id="c6b6e-109">Information</span></span>|  
|<span data-ttu-id="c6b6e-110">通道</span><span class="sxs-lookup"><span data-stu-id="c6b6e-110">Channel</span></span>|<span data-ttu-id="c6b6e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c6b6e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c6b6e-112">描述</span><span class="sxs-lookup"><span data-stu-id="c6b6e-112">Description</span></span>  
 <span data-ttu-id="c6b6e-113">表示 SQL 提供者正在重試 SQL 命令，因為發生 SQL 錯誤。</span><span class="sxs-lookup"><span data-stu-id="c6b6e-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c6b6e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="c6b6e-114">Message</span></span>  
 <span data-ttu-id="c6b6e-115">重試 SQL 命令，因為出現 SQL 錯誤代碼 %1。</span><span class="sxs-lookup"><span data-stu-id="c6b6e-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c6b6e-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c6b6e-116">Details</span></span>  
  
|<span data-ttu-id="c6b6e-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="c6b6e-117">Data Item Name</span></span>|<span data-ttu-id="c6b6e-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="c6b6e-118">Data Item Type</span></span>|<span data-ttu-id="c6b6e-119">描述</span><span class="sxs-lookup"><span data-stu-id="c6b6e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c6b6e-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="c6b6e-120">ErrorNumber</span></span>|<span data-ttu-id="c6b6e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6b6e-121">xs:string</span></span>|<span data-ttu-id="c6b6e-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="c6b6e-122">The SQL error number.</span></span>|  
|<span data-ttu-id="c6b6e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c6b6e-123">AppDomain</span></span>|<span data-ttu-id="c6b6e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c6b6e-124">xs:string</span></span>|<span data-ttu-id="c6b6e-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="c6b6e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
