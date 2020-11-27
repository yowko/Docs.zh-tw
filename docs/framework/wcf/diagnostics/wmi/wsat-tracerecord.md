---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 0409277821a7cca3f97fcec1bb383aba9583a1f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262212"
---
# <a name="wsat_tracerecord"></a><span data-ttu-id="fd75d-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="fd75d-102">WSAT_TraceRecord</span></span>

<span data-ttu-id="fd75d-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="fd75d-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd75d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd75d-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fd75d-105">方法</span><span class="sxs-lookup"><span data-stu-id="fd75d-105">Methods</span></span>  

 <span data-ttu-id="fd75d-106">WSAT_TraceRecord 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="fd75d-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fd75d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fd75d-107">Properties</span></span>  

 <span data-ttu-id="fd75d-108">WSAT_TraceRecord 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fd75d-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="fd75d-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="fd75d-109">ActivityID</span></span>  

 <span data-ttu-id="fd75d-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="fd75d-110">Data type: object</span></span>  
<span data-ttu-id="fd75d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fd75d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd75d-112">追蹤記錄的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="fd75d-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="fd75d-113">EventID</span><span class="sxs-lookup"><span data-stu-id="fd75d-113">EventID</span></span>  

 <span data-ttu-id="fd75d-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="fd75d-114">Data type: sint32</span></span>  
<span data-ttu-id="fd75d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fd75d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd75d-116">追蹤記錄的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="fd75d-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="fd75d-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="fd75d-117">TraceRecord</span></span>  

 <span data-ttu-id="fd75d-118">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="fd75d-118">Data type: string</span></span>  
<span data-ttu-id="fd75d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fd75d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd75d-120">追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="fd75d-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd75d-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="fd75d-121">Requirements</span></span>  
  
|<span data-ttu-id="fd75d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="fd75d-122">MOF</span></span>|<span data-ttu-id="fd75d-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="fd75d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fd75d-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="fd75d-124">Namespace</span></span>|<span data-ttu-id="fd75d-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="fd75d-125">Defined in root\ServiceModel</span></span>|
