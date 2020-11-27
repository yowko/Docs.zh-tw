---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: d3f27c6ed28efe9d099dcedfc676b839ae9b1dee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275836"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="d6b5e-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="d6b5e-102">4202 - StartSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="d6b5e-103">屬性</span><span class="sxs-lookup"><span data-stu-id="d6b5e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6b5e-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="d6b5e-104">ID</span></span>|<span data-ttu-id="d6b5e-105">4202</span><span class="sxs-lookup"><span data-stu-id="d6b5e-105">4202</span></span>|  
|<span data-ttu-id="d6b5e-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d6b5e-106">Keywords</span></span>|<span data-ttu-id="d6b5e-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d6b5e-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d6b5e-108">層級</span><span class="sxs-lookup"><span data-stu-id="d6b5e-108">Level</span></span>|<span data-ttu-id="d6b5e-109">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="d6b5e-109">Verbose</span></span>|  
|<span data-ttu-id="d6b5e-110">通路</span><span class="sxs-lookup"><span data-stu-id="d6b5e-110">Channel</span></span>|<span data-ttu-id="d6b5e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d6b5e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6b5e-112">描述</span><span class="sxs-lookup"><span data-stu-id="d6b5e-112">Description</span></span>  

 <span data-ttu-id="d6b5e-113">表示正在執行 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="d6b5e-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6b5e-114">訊息</span><span class="sxs-lookup"><span data-stu-id="d6b5e-114">Message</span></span>  

 <span data-ttu-id="d6b5e-115">開始 SQL 命令執行：%1</span><span class="sxs-lookup"><span data-stu-id="d6b5e-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6b5e-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d6b5e-116">Details</span></span>  
  
|<span data-ttu-id="d6b5e-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="d6b5e-117">Data Item Name</span></span>|<span data-ttu-id="d6b5e-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="d6b5e-118">Data Item Type</span></span>|<span data-ttu-id="d6b5e-119">描述</span><span class="sxs-lookup"><span data-stu-id="d6b5e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6b5e-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="d6b5e-120">SqlCommand</span></span>|<span data-ttu-id="d6b5e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d6b5e-121">xs:string</span></span>|<span data-ttu-id="d6b5e-122">所執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="d6b5e-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="d6b5e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d6b5e-123">AppDomain</span></span>|<span data-ttu-id="d6b5e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d6b5e-124">xs:string</span></span>|<span data-ttu-id="d6b5e-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d6b5e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
