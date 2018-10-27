---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194770"
---
# <a name="wsattracerecord"></a><span data-ttu-id="75fc2-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="75fc2-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="75fc2-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="75fc2-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75fc2-104">語法</span><span class="sxs-lookup"><span data-stu-id="75fc2-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="75fc2-105">方法</span><span class="sxs-lookup"><span data-stu-id="75fc2-105">Methods</span></span>  
 <span data-ttu-id="75fc2-106">WSAT_TraceRecord 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="75fc2-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="75fc2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="75fc2-107">Properties</span></span>  
 <span data-ttu-id="75fc2-108">WSAT_TraceRecord 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="75fc2-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="75fc2-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="75fc2-109">ActivityID</span></span>  
 <span data-ttu-id="75fc2-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="75fc2-110">Data type: object</span></span>  
<span data-ttu-id="75fc2-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75fc2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75fc2-112">追蹤記錄的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="75fc2-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="75fc2-113">事件 ID</span><span class="sxs-lookup"><span data-stu-id="75fc2-113">EventID</span></span>  
 <span data-ttu-id="75fc2-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="75fc2-114">Data type: sint32</span></span>  
<span data-ttu-id="75fc2-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75fc2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75fc2-116">追蹤記錄的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="75fc2-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="75fc2-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="75fc2-117">TraceRecord</span></span>  
 <span data-ttu-id="75fc2-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="75fc2-118">Data type: string</span></span>  
<span data-ttu-id="75fc2-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="75fc2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75fc2-120">追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="75fc2-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75fc2-121">需求</span><span class="sxs-lookup"><span data-stu-id="75fc2-121">Requirements</span></span>  
  
|<span data-ttu-id="75fc2-122">MOF</span><span class="sxs-lookup"><span data-stu-id="75fc2-122">MOF</span></span>|<span data-ttu-id="75fc2-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="75fc2-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="75fc2-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="75fc2-124">Namespace</span></span>|<span data-ttu-id="75fc2-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="75fc2-125">Defined in root\ServiceModel</span></span>|
