---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923405"
---
# <a name="wsattracerecord"></a><span data-ttu-id="3aac1-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="3aac1-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="3aac1-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="3aac1-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aac1-104">語法</span><span class="sxs-lookup"><span data-stu-id="3aac1-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3aac1-105">方法</span><span class="sxs-lookup"><span data-stu-id="3aac1-105">Methods</span></span>  
 <span data-ttu-id="3aac1-106">WSAT_TraceRecord 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="3aac1-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3aac1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3aac1-107">Properties</span></span>  
 <span data-ttu-id="3aac1-108">WSAT_TraceRecord 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3aac1-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="3aac1-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="3aac1-109">ActivityID</span></span>  
 <span data-ttu-id="3aac1-110">資料型別：物件</span><span class="sxs-lookup"><span data-stu-id="3aac1-110">Data type: object</span></span>  
<span data-ttu-id="3aac1-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3aac1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3aac1-112">追蹤記錄的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="3aac1-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="3aac1-113">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3aac1-113">EventID</span></span>  
 <span data-ttu-id="3aac1-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="3aac1-114">Data type: sint32</span></span>  
<span data-ttu-id="3aac1-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3aac1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3aac1-116">追蹤記錄的事件識別碼。</span><span class="sxs-lookup"><span data-stu-id="3aac1-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="3aac1-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="3aac1-117">TraceRecord</span></span>  
 <span data-ttu-id="3aac1-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="3aac1-118">Data type: string</span></span>  
<span data-ttu-id="3aac1-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="3aac1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3aac1-120">追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="3aac1-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aac1-121">需求</span><span class="sxs-lookup"><span data-stu-id="3aac1-121">Requirements</span></span>  
  
|<span data-ttu-id="3aac1-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3aac1-122">MOF</span></span>|<span data-ttu-id="3aac1-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="3aac1-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3aac1-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="3aac1-124">Namespace</span></span>|<span data-ttu-id="3aac1-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="3aac1-125">Defined in root\ServiceModel</span></span>|
