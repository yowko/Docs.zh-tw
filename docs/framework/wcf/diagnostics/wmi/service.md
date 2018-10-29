---
title: 服務
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196904"
---
# <a name="service"></a><span data-ttu-id="da18f-102">服務</span><span class="sxs-lookup"><span data-stu-id="da18f-102">Service</span></span>
<span data-ttu-id="da18f-103">服務</span><span class="sxs-lookup"><span data-stu-id="da18f-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da18f-104">語法</span><span class="sxs-lookup"><span data-stu-id="da18f-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="da18f-105">方法</span><span class="sxs-lookup"><span data-stu-id="da18f-105">Methods</span></span>  
 <span data-ttu-id="da18f-106">此服務類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="da18f-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="da18f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="da18f-107">Properties</span></span>  
 <span data-ttu-id="da18f-108">此服務類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="da18f-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="da18f-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="da18f-109">BaseAddresses</span></span>  
 <span data-ttu-id="da18f-110">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="da18f-110">Data type: string array</span></span>  
  
 <span data-ttu-id="da18f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-112">由服務使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="da18f-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="da18f-113">「行為」</span><span class="sxs-lookup"><span data-stu-id="da18f-113">Behaviors</span></span>  
 <span data-ttu-id="da18f-114">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="da18f-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="da18f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-116">與此服務關聯的行為。</span><span class="sxs-lookup"><span data-stu-id="da18f-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="da18f-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="da18f-117">ConfigurationName</span></span>  
 <span data-ttu-id="da18f-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="da18f-118">Data type: string</span></span>  
  
 <span data-ttu-id="da18f-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="da18f-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="da18f-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="da18f-121">CounterInstanceName</span></span>  
 <span data-ttu-id="da18f-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="da18f-122">Data type: string</span></span>  
  
 <span data-ttu-id="da18f-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-124">服務效能計數器之執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="da18f-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="da18f-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="da18f-125">DistinguishedName</span></span>  
 <span data-ttu-id="da18f-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="da18f-126">Data type: string</span></span>  
  
 <span data-ttu-id="da18f-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-128">位址的服務名稱。</span><span class="sxs-lookup"><span data-stu-id="da18f-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="da18f-129">延伸模組</span><span class="sxs-lookup"><span data-stu-id="da18f-129">Extensions</span></span>  
 <span data-ttu-id="da18f-130">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="da18f-130">Data type: string array</span></span>  
  
 <span data-ttu-id="da18f-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-132">服務執行個體擴充的執行個體內容。</span><span class="sxs-lookup"><span data-stu-id="da18f-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="da18f-133">中繼資料</span><span class="sxs-lookup"><span data-stu-id="da18f-133">Metadata</span></span>  
 <span data-ttu-id="da18f-134">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="da18f-134">Data type: string array</span></span>  
  
 <span data-ttu-id="da18f-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-136">服務中繼資料設定。</span><span class="sxs-lookup"><span data-stu-id="da18f-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="da18f-137">名稱</span><span class="sxs-lookup"><span data-stu-id="da18f-137">Name</span></span>  
 <span data-ttu-id="da18f-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="da18f-138">Data type: string</span></span>  
  
 <span data-ttu-id="da18f-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-140">這個服務的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="da18f-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="da18f-141">命名空間</span><span class="sxs-lookup"><span data-stu-id="da18f-141">Namespace</span></span>  
 <span data-ttu-id="da18f-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="da18f-142">Data type: string</span></span>  
  
 <span data-ttu-id="da18f-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-144">服務的命名空間。</span><span class="sxs-lookup"><span data-stu-id="da18f-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="da18f-145">Opened</span><span class="sxs-lookup"><span data-stu-id="da18f-145">Opened</span></span>  
 <span data-ttu-id="da18f-146">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="da18f-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="da18f-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-148">服務開啟的時間。</span><span class="sxs-lookup"><span data-stu-id="da18f-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="da18f-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="da18f-149">OutgoingChannels</span></span>  
 <span data-ttu-id="da18f-150">資料類型：通道陣列</span><span class="sxs-lookup"><span data-stu-id="da18f-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="da18f-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-152">從服務執行個體傳出的通道。</span><span class="sxs-lookup"><span data-stu-id="da18f-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="da18f-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="da18f-153">ProcessId</span></span>  
 <span data-ttu-id="da18f-154">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="da18f-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="da18f-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="da18f-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="da18f-156">裝載服務之處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="da18f-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da18f-157">需求</span><span class="sxs-lookup"><span data-stu-id="da18f-157">Requirements</span></span>  
  
|<span data-ttu-id="da18f-158">MOF</span><span class="sxs-lookup"><span data-stu-id="da18f-158">MOF</span></span>|<span data-ttu-id="da18f-159">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="da18f-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="da18f-160">命名空間</span><span class="sxs-lookup"><span data-stu-id="da18f-160">Namespace</span></span>|<span data-ttu-id="da18f-161">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="da18f-161">Defined in root\ServiceModel</span></span>|
