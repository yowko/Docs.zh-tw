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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="6228b-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="6228b-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="6228b-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="6228b-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6228b-104">語法</span><span class="sxs-lookup"><span data-stu-id="6228b-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6228b-105">方法</span><span class="sxs-lookup"><span data-stu-id="6228b-105">Methods</span></span>  
 <span data-ttu-id="6228b-106">WSAT_TraceRecord 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="6228b-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6228b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6228b-107">Properties</span></span>  
 <span data-ttu-id="6228b-108">WSAT_TraceRecord 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6228b-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="6228b-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="6228b-109">ActivityID</span></span>  
 <span data-ttu-id="6228b-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="6228b-110">Data type: object</span></span>  
<span data-ttu-id="6228b-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6228b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6228b-112">追蹤記錄的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="6228b-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="6228b-113">EventID</span><span class="sxs-lookup"><span data-stu-id="6228b-113">EventID</span></span>  
 <span data-ttu-id="6228b-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="6228b-114">Data type: sint32</span></span>  
<span data-ttu-id="6228b-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6228b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6228b-116">追蹤記錄的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="6228b-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="6228b-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="6228b-117">TraceRecord</span></span>  
 <span data-ttu-id="6228b-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6228b-118">Data type: string</span></span>  
<span data-ttu-id="6228b-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6228b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6228b-120">追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="6228b-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6228b-121">需求</span><span class="sxs-lookup"><span data-stu-id="6228b-121">Requirements</span></span>  
  
|<span data-ttu-id="6228b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6228b-122">MOF</span></span>|<span data-ttu-id="6228b-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="6228b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6228b-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="6228b-124">Namespace</span></span>|<span data-ttu-id="6228b-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="6228b-125">Defined in root\ServiceModel</span></span>|
