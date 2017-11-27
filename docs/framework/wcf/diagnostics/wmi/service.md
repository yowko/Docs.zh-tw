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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bd784b470810e16b86ba7537b1f45681ac3e1ed1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="service"></a><span data-ttu-id="25597-102">服務</span><span class="sxs-lookup"><span data-stu-id="25597-102">Service</span></span>
<span data-ttu-id="25597-103">服務</span><span class="sxs-lookup"><span data-stu-id="25597-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25597-104">語法</span><span class="sxs-lookup"><span data-stu-id="25597-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="25597-105">方法</span><span class="sxs-lookup"><span data-stu-id="25597-105">Methods</span></span>  
 <span data-ttu-id="25597-106">此服務類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="25597-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="25597-107">屬性</span><span class="sxs-lookup"><span data-stu-id="25597-107">Properties</span></span>  
 <span data-ttu-id="25597-108">此服務類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="25597-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="25597-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="25597-109">BaseAddresses</span></span>  
 <span data-ttu-id="25597-110">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="25597-110">Data type: string array</span></span>  
  
 <span data-ttu-id="25597-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-112">由服務使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="25597-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="25597-113">行為</span><span class="sxs-lookup"><span data-stu-id="25597-113">Behaviors</span></span>  
 <span data-ttu-id="25597-114">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="25597-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="25597-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-116">與此服務關聯的行為。</span><span class="sxs-lookup"><span data-stu-id="25597-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="25597-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="25597-117">ConfigurationName</span></span>  
 <span data-ttu-id="25597-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="25597-118">Data type: string</span></span>  
  
 <span data-ttu-id="25597-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="25597-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="25597-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="25597-121">CounterInstanceName</span></span>  
 <span data-ttu-id="25597-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="25597-122">Data type: string</span></span>  
  
 <span data-ttu-id="25597-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-124">服務效能計數器之執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="25597-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="25597-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="25597-125">DistinguishedName</span></span>  
 <span data-ttu-id="25597-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="25597-126">Data type: string</span></span>  
  
 <span data-ttu-id="25597-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-128">位址的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="25597-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="25597-129">擴充功能</span><span class="sxs-lookup"><span data-stu-id="25597-129">Extensions</span></span>  
 <span data-ttu-id="25597-130">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="25597-130">Data type: string array</span></span>  
  
 <span data-ttu-id="25597-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-132">服務執行個體擴充的執行個體內容。</span><span class="sxs-lookup"><span data-stu-id="25597-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="25597-133">中繼資料</span><span class="sxs-lookup"><span data-stu-id="25597-133">Metadata</span></span>  
 <span data-ttu-id="25597-134">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="25597-134">Data type: string array</span></span>  
  
 <span data-ttu-id="25597-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-136">服務中繼資料設定。</span><span class="sxs-lookup"><span data-stu-id="25597-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="25597-137">名稱</span><span class="sxs-lookup"><span data-stu-id="25597-137">Name</span></span>  
 <span data-ttu-id="25597-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="25597-138">Data type: string</span></span>  
  
 <span data-ttu-id="25597-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-140">這個服務的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="25597-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="25597-141">命名空間</span><span class="sxs-lookup"><span data-stu-id="25597-141">Namespace</span></span>  
 <span data-ttu-id="25597-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="25597-142">Data type: string</span></span>  
  
 <span data-ttu-id="25597-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-144">服務的命名空間。</span><span class="sxs-lookup"><span data-stu-id="25597-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="25597-145">Opened</span><span class="sxs-lookup"><span data-stu-id="25597-145">Opened</span></span>  
 <span data-ttu-id="25597-146">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="25597-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="25597-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-148">服務開啟的時間。</span><span class="sxs-lookup"><span data-stu-id="25597-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="25597-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="25597-149">OutgoingChannels</span></span>  
 <span data-ttu-id="25597-150">資料類型：通道陣列</span><span class="sxs-lookup"><span data-stu-id="25597-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="25597-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-152">從服務執行個體傳出的通道。</span><span class="sxs-lookup"><span data-stu-id="25597-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="25597-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="25597-153">ProcessId</span></span>  
 <span data-ttu-id="25597-154">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="25597-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="25597-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="25597-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="25597-156">裝載服務之處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="25597-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25597-157">需求</span><span class="sxs-lookup"><span data-stu-id="25597-157">Requirements</span></span>  
  
|<span data-ttu-id="25597-158">MOF</span><span class="sxs-lookup"><span data-stu-id="25597-158">MOF</span></span>|<span data-ttu-id="25597-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="25597-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="25597-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="25597-160">Namespace</span></span>|<span data-ttu-id="25597-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="25597-161">Defined in root\ServiceModel</span></span>|
