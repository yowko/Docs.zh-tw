---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 088754cb15c2e55faa1d43a1da1c79ddcddd69f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280412"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="215d7-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="215d7-102">4208 - RetryingSqlCommandDueToSqlError</span></span>

## <a name="properties"></a><span data-ttu-id="215d7-103">屬性</span><span class="sxs-lookup"><span data-stu-id="215d7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="215d7-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="215d7-104">ID</span></span>|<span data-ttu-id="215d7-105">4208</span><span class="sxs-lookup"><span data-stu-id="215d7-105">4208</span></span>|  
|<span data-ttu-id="215d7-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="215d7-106">Keywords</span></span>|<span data-ttu-id="215d7-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="215d7-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="215d7-108">層級</span><span class="sxs-lookup"><span data-stu-id="215d7-108">Level</span></span>|<span data-ttu-id="215d7-109">資訊</span><span class="sxs-lookup"><span data-stu-id="215d7-109">Information</span></span>|  
|<span data-ttu-id="215d7-110">通路</span><span class="sxs-lookup"><span data-stu-id="215d7-110">Channel</span></span>|<span data-ttu-id="215d7-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="215d7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="215d7-112">描述</span><span class="sxs-lookup"><span data-stu-id="215d7-112">Description</span></span>  

 <span data-ttu-id="215d7-113">表示 SQL 提供者正在重試 SQL 命令，因為發生 SQL 錯誤。</span><span class="sxs-lookup"><span data-stu-id="215d7-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="215d7-114">訊息</span><span class="sxs-lookup"><span data-stu-id="215d7-114">Message</span></span>  

 <span data-ttu-id="215d7-115">重試 SQL 命令，因為出現 SQL 錯誤代碼 %1。</span><span class="sxs-lookup"><span data-stu-id="215d7-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="215d7-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="215d7-116">Details</span></span>  
  
|<span data-ttu-id="215d7-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="215d7-117">Data Item Name</span></span>|<span data-ttu-id="215d7-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="215d7-118">Data Item Type</span></span>|<span data-ttu-id="215d7-119">描述</span><span class="sxs-lookup"><span data-stu-id="215d7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="215d7-120">錯誤號碼</span><span class="sxs-lookup"><span data-stu-id="215d7-120">ErrorNumber</span></span>|<span data-ttu-id="215d7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="215d7-121">xs:string</span></span>|<span data-ttu-id="215d7-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="215d7-122">The SQL error number.</span></span>|  
|<span data-ttu-id="215d7-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="215d7-123">AppDomain</span></span>|<span data-ttu-id="215d7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="215d7-124">xs:string</span></span>|<span data-ttu-id="215d7-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="215d7-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
