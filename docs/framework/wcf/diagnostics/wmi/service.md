---
title: "服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f7b631ede7bd011a92003dc5f6083c1c427d990e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="service"></a><span data-ttu-id="eb10e-102">服務</span><span class="sxs-lookup"><span data-stu-id="eb10e-102">Service</span></span>
<span data-ttu-id="eb10e-103">服務</span><span class="sxs-lookup"><span data-stu-id="eb10e-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb10e-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb10e-104">Syntax</span></span>  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eb10e-105">方法</span><span class="sxs-lookup"><span data-stu-id="eb10e-105">Methods</span></span>  
 <span data-ttu-id="eb10e-106">此服務類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="eb10e-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="eb10e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="eb10e-107">Properties</span></span>  
 <span data-ttu-id="eb10e-108">此服務類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="eb10e-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="eb10e-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="eb10e-109">BaseAddresses</span></span>  
 <span data-ttu-id="eb10e-110">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="eb10e-110">Data type: string array</span></span>  
  
 <span data-ttu-id="eb10e-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-112">由服務使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="eb10e-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="eb10e-113">「行為」</span><span class="sxs-lookup"><span data-stu-id="eb10e-113">Behaviors</span></span>  
 <span data-ttu-id="eb10e-114">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="eb10e-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="eb10e-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-116">與此服務關聯的行為。</span><span class="sxs-lookup"><span data-stu-id="eb10e-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="eb10e-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="eb10e-117">ConfigurationName</span></span>  
 <span data-ttu-id="eb10e-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="eb10e-118">Data type: string</span></span>  
  
 <span data-ttu-id="eb10e-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="eb10e-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="eb10e-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="eb10e-121">CounterInstanceName</span></span>  
 <span data-ttu-id="eb10e-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="eb10e-122">Data type: string</span></span>  
  
 <span data-ttu-id="eb10e-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-124">服務效能計數器之執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="eb10e-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="eb10e-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="eb10e-125">DistinguishedName</span></span>  
 <span data-ttu-id="eb10e-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="eb10e-126">Data type: string</span></span>  
  
 <span data-ttu-id="eb10e-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-128">位址的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="eb10e-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="eb10e-129">延伸模組</span><span class="sxs-lookup"><span data-stu-id="eb10e-129">Extensions</span></span>  
 <span data-ttu-id="eb10e-130">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="eb10e-130">Data type: string array</span></span>  
  
 <span data-ttu-id="eb10e-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-132">服務執行個體擴充的執行個體內容。</span><span class="sxs-lookup"><span data-stu-id="eb10e-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="eb10e-133">中繼資料</span><span class="sxs-lookup"><span data-stu-id="eb10e-133">Metadata</span></span>  
 <span data-ttu-id="eb10e-134">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="eb10e-134">Data type: string array</span></span>  
  
 <span data-ttu-id="eb10e-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-136">服務中繼資料設定。</span><span class="sxs-lookup"><span data-stu-id="eb10e-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="eb10e-137">名稱</span><span class="sxs-lookup"><span data-stu-id="eb10e-137">Name</span></span>  
 <span data-ttu-id="eb10e-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="eb10e-138">Data type: string</span></span>  
  
 <span data-ttu-id="eb10e-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-140">這個服務的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="eb10e-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="eb10e-141">命名空間</span><span class="sxs-lookup"><span data-stu-id="eb10e-141">Namespace</span></span>  
 <span data-ttu-id="eb10e-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="eb10e-142">Data type: string</span></span>  
  
 <span data-ttu-id="eb10e-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-144">服務的命名空間。</span><span class="sxs-lookup"><span data-stu-id="eb10e-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="eb10e-145">Opened</span><span class="sxs-lookup"><span data-stu-id="eb10e-145">Opened</span></span>  
 <span data-ttu-id="eb10e-146">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="eb10e-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="eb10e-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-148">服務開啟的時間。</span><span class="sxs-lookup"><span data-stu-id="eb10e-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="eb10e-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="eb10e-149">OutgoingChannels</span></span>  
 <span data-ttu-id="eb10e-150">資料類型：通道陣列</span><span class="sxs-lookup"><span data-stu-id="eb10e-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="eb10e-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-152">從服務執行個體傳出的通道。</span><span class="sxs-lookup"><span data-stu-id="eb10e-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="eb10e-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="eb10e-153">ProcessId</span></span>  
 <span data-ttu-id="eb10e-154">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="eb10e-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="eb10e-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="eb10e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb10e-156">裝載服務之處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="eb10e-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb10e-157">需求</span><span class="sxs-lookup"><span data-stu-id="eb10e-157">Requirements</span></span>  
  
|<span data-ttu-id="eb10e-158">MOF</span><span class="sxs-lookup"><span data-stu-id="eb10e-158">MOF</span></span>|<span data-ttu-id="eb10e-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="eb10e-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="eb10e-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="eb10e-160">Namespace</span></span>|<span data-ttu-id="eb10e-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="eb10e-161">Defined in root\ServiceModel</span></span>|
