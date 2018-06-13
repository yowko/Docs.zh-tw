---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511588"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="8f542-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="8f542-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="8f542-103">屬性</span><span class="sxs-lookup"><span data-stu-id="8f542-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f542-104">ID</span><span class="sxs-lookup"><span data-stu-id="8f542-104">ID</span></span>|<span data-ttu-id="8f542-105">4208</span><span class="sxs-lookup"><span data-stu-id="8f542-105">4208</span></span>|  
|<span data-ttu-id="8f542-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="8f542-106">Keywords</span></span>|<span data-ttu-id="8f542-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="8f542-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="8f542-108">層級</span><span class="sxs-lookup"><span data-stu-id="8f542-108">Level</span></span>|<span data-ttu-id="8f542-109">資訊</span><span class="sxs-lookup"><span data-stu-id="8f542-109">Information</span></span>|  
|<span data-ttu-id="8f542-110">通道</span><span class="sxs-lookup"><span data-stu-id="8f542-110">Channel</span></span>|<span data-ttu-id="8f542-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8f542-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8f542-112">描述</span><span class="sxs-lookup"><span data-stu-id="8f542-112">Description</span></span>  
 <span data-ttu-id="8f542-113">表示 SQL 提供者正在重試 SQL 命令，因為發生 SQL 錯誤。</span><span class="sxs-lookup"><span data-stu-id="8f542-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8f542-114">訊息</span><span class="sxs-lookup"><span data-stu-id="8f542-114">Message</span></span>  
 <span data-ttu-id="8f542-115">重試 SQL 命令，因為出現 SQL 錯誤代碼 %1。</span><span class="sxs-lookup"><span data-stu-id="8f542-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8f542-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8f542-116">Details</span></span>  
  
|<span data-ttu-id="8f542-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="8f542-117">Data Item Name</span></span>|<span data-ttu-id="8f542-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="8f542-118">Data Item Type</span></span>|<span data-ttu-id="8f542-119">描述</span><span class="sxs-lookup"><span data-stu-id="8f542-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8f542-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="8f542-120">ErrorNumber</span></span>|<span data-ttu-id="8f542-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8f542-121">xs:string</span></span>|<span data-ttu-id="8f542-122">SQL 錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="8f542-122">The SQL error number.</span></span>|  
|<span data-ttu-id="8f542-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8f542-123">AppDomain</span></span>|<span data-ttu-id="8f542-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8f542-124">xs:string</span></span>|<span data-ttu-id="8f542-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="8f542-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
