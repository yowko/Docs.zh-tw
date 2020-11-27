---
title: 端點
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: ceb4e4b41502b00d7bb21f1ecbd8249fccf1ce3b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288810"
---
# <a name="endpoint"></a><span data-ttu-id="66311-102">端點</span><span class="sxs-lookup"><span data-stu-id="66311-102">Endpoint</span></span>

<span data-ttu-id="66311-103">端點</span><span class="sxs-lookup"><span data-stu-id="66311-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66311-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="66311-104">Syntax</span></span>  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="66311-105">方法</span><span class="sxs-lookup"><span data-stu-id="66311-105">Methods</span></span>  

 <span data-ttu-id="66311-106">Endpoint 類別定義下列方法。</span><span class="sxs-lookup"><span data-stu-id="66311-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="66311-107">方法</span><span class="sxs-lookup"><span data-stu-id="66311-107">Method</span></span>|<span data-ttu-id="66311-108">描述</span><span class="sxs-lookup"><span data-stu-id="66311-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66311-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="66311-109">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="66311-110">擷取作業效能計數器執行個體名稱</span><span class="sxs-lookup"><span data-stu-id="66311-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="66311-111">屬性</span><span class="sxs-lookup"><span data-stu-id="66311-111">Properties</span></span>  

 <span data-ttu-id="66311-112">Endpoint 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="66311-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="66311-113">位址</span><span class="sxs-lookup"><span data-stu-id="66311-113">Address</span></span>  

 <span data-ttu-id="66311-114">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="66311-114">Data type: string</span></span>  
  
 <span data-ttu-id="66311-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-116">包含端點位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="66311-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="66311-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="66311-117">AddressHeaders</span></span>  

 <span data-ttu-id="66311-118">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="66311-118">Data type: string array</span></span>  
  
 <span data-ttu-id="66311-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-120">附加到此端點之位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="66311-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="66311-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="66311-121">AddressIdentity</span></span>  

 <span data-ttu-id="66311-122">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="66311-122">Data type: string</span></span>  
  
 <span data-ttu-id="66311-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-124">端點的身分識別。</span><span class="sxs-lookup"><span data-stu-id="66311-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="66311-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="66311-125">AppDomainId</span></span>  

 <span data-ttu-id="66311-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="66311-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="66311-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-128">裝載端點之 appdomain 的 appdomain 識別碼。</span><span class="sxs-lookup"><span data-stu-id="66311-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="66311-129">行為</span><span class="sxs-lookup"><span data-stu-id="66311-129">Behaviors</span></span>  

 <span data-ttu-id="66311-130">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="66311-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="66311-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-132">此端點實作之行為的集合。</span><span class="sxs-lookup"><span data-stu-id="66311-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="66311-133">繫結</span><span class="sxs-lookup"><span data-stu-id="66311-133">Binding</span></span>  

 <span data-ttu-id="66311-134">資料型別：繫結</span><span class="sxs-lookup"><span data-stu-id="66311-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="66311-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-136">此端點所使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="66311-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="66311-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="66311-137">ContractName</span></span>  

 <span data-ttu-id="66311-138">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="66311-138">Data type: string</span></span>  
  
 <span data-ttu-id="66311-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-140">指定公開此端點之合約的字串。</span><span class="sxs-lookup"><span data-stu-id="66311-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="66311-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="66311-141">CounterInstanceName</span></span>  

 <span data-ttu-id="66311-142">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="66311-142">Data type: string</span></span>  
  
 <span data-ttu-id="66311-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-144">端點之效能計數器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="66311-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="66311-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="66311-145">ListenUri</span></span>  

 <span data-ttu-id="66311-146">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="66311-146">Data type: string</span></span>  
  
 <span data-ttu-id="66311-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-148">端點接聽的 Uri。</span><span class="sxs-lookup"><span data-stu-id="66311-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="66311-149">Name</span><span class="sxs-lookup"><span data-stu-id="66311-149">Name</span></span>  

 <span data-ttu-id="66311-150">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="66311-150">Data type: string</span></span>  
  
 <span data-ttu-id="66311-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-152">此端點的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="66311-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="66311-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="66311-153">ProcessId</span></span>  

 <span data-ttu-id="66311-154">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="66311-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="66311-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-156">裝載端點之處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="66311-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="66311-157">ref</span><span class="sxs-lookup"><span data-stu-id="66311-157">ref</span></span>  

 <span data-ttu-id="66311-158">資料型別：合約</span><span class="sxs-lookup"><span data-stu-id="66311-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="66311-159">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="66311-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66311-160">此端點公開的合約。</span><span class="sxs-lookup"><span data-stu-id="66311-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66311-161">規格需求</span><span class="sxs-lookup"><span data-stu-id="66311-161">Requirements</span></span>  
  
|<span data-ttu-id="66311-162">MOF</span><span class="sxs-lookup"><span data-stu-id="66311-162">MOF</span></span>|<span data-ttu-id="66311-163">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="66311-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="66311-164">命名空間</span><span class="sxs-lookup"><span data-stu-id="66311-164">Namespace</span></span>|<span data-ttu-id="66311-165">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="66311-165">Defined in root\ServiceModel</span></span>|
