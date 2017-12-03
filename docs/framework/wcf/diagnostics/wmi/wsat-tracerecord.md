---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="740e0-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="740e0-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="740e0-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="740e0-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="740e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="740e0-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="740e0-105">方法</span><span class="sxs-lookup"><span data-stu-id="740e0-105">Methods</span></span>  
 <span data-ttu-id="740e0-106">WSAT_TraceRecord 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="740e0-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="740e0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="740e0-107">Properties</span></span>  
 <span data-ttu-id="740e0-108">WSAT_TraceRecord 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="740e0-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="740e0-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="740e0-109">ActivityID</span></span>  
 <span data-ttu-id="740e0-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="740e0-110">Data type: object</span></span>  
<span data-ttu-id="740e0-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="740e0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="740e0-112">追蹤記錄的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="740e0-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="740e0-113">EventID</span><span class="sxs-lookup"><span data-stu-id="740e0-113">EventID</span></span>  
 <span data-ttu-id="740e0-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="740e0-114">Data type: sint32</span></span>  
<span data-ttu-id="740e0-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="740e0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="740e0-116">追蹤記錄的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="740e0-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="740e0-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="740e0-117">TraceRecord</span></span>  
 <span data-ttu-id="740e0-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="740e0-118">Data type: string</span></span>  
<span data-ttu-id="740e0-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="740e0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="740e0-120">追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="740e0-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="740e0-121">需求</span><span class="sxs-lookup"><span data-stu-id="740e0-121">Requirements</span></span>  
  
|<span data-ttu-id="740e0-122">MOF</span><span class="sxs-lookup"><span data-stu-id="740e0-122">MOF</span></span>|<span data-ttu-id="740e0-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="740e0-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="740e0-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="740e0-124">Namespace</span></span>|<span data-ttu-id="740e0-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="740e0-125">Defined in root\ServiceModel</span></span>|
