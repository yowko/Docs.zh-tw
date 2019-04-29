---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: 09e079864369115c773c58c451fc5e0a33a3ae9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774370"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="f316b-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="f316b-102">4202 - StartSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="f316b-103">屬性</span><span class="sxs-lookup"><span data-stu-id="f316b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f316b-104">識別碼</span><span class="sxs-lookup"><span data-stu-id="f316b-104">ID</span></span>|<span data-ttu-id="f316b-105">4202</span><span class="sxs-lookup"><span data-stu-id="f316b-105">4202</span></span>|  
|<span data-ttu-id="f316b-106">關鍵字</span><span class="sxs-lookup"><span data-stu-id="f316b-106">Keywords</span></span>|<span data-ttu-id="f316b-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f316b-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f316b-108">層級</span><span class="sxs-lookup"><span data-stu-id="f316b-108">Level</span></span>|<span data-ttu-id="f316b-109">詳細資訊</span><span class="sxs-lookup"><span data-stu-id="f316b-109">Verbose</span></span>|  
|<span data-ttu-id="f316b-110">通道</span><span class="sxs-lookup"><span data-stu-id="f316b-110">Channel</span></span>|<span data-ttu-id="f316b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f316b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f316b-112">描述</span><span class="sxs-lookup"><span data-stu-id="f316b-112">Description</span></span>  
 <span data-ttu-id="f316b-113">表示正在執行 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="f316b-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f316b-114">訊息</span><span class="sxs-lookup"><span data-stu-id="f316b-114">Message</span></span>  
 <span data-ttu-id="f316b-115">開始 SQL 命令執行：%1</span><span class="sxs-lookup"><span data-stu-id="f316b-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="f316b-116">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f316b-116">Details</span></span>  
  
|<span data-ttu-id="f316b-117">資料項目名稱</span><span class="sxs-lookup"><span data-stu-id="f316b-117">Data Item Name</span></span>|<span data-ttu-id="f316b-118">資料項目型別</span><span class="sxs-lookup"><span data-stu-id="f316b-118">Data Item Type</span></span>|<span data-ttu-id="f316b-119">描述</span><span class="sxs-lookup"><span data-stu-id="f316b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f316b-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="f316b-120">SqlCommand</span></span>|<span data-ttu-id="f316b-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f316b-121">xs:string</span></span>|<span data-ttu-id="f316b-122">所執行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="f316b-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="f316b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f316b-123">AppDomain</span></span>|<span data-ttu-id="f316b-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f316b-124">xs:string</span></span>|<span data-ttu-id="f316b-125">由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="f316b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
