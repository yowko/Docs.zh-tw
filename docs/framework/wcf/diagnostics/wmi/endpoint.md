---
title: "端點"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed3c01f6943ec2958da56777ac0d6223fff66ab0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint"></a><span data-ttu-id="40e2b-102">端點</span><span class="sxs-lookup"><span data-stu-id="40e2b-102">Endpoint</span></span>
<span data-ttu-id="40e2b-103">端點</span><span class="sxs-lookup"><span data-stu-id="40e2b-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40e2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="40e2b-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="40e2b-105">方法</span><span class="sxs-lookup"><span data-stu-id="40e2b-105">Methods</span></span>  
 <span data-ttu-id="40e2b-106">Endpoint 類別定義下列方法。</span><span class="sxs-lookup"><span data-stu-id="40e2b-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="40e2b-107">方法</span><span class="sxs-lookup"><span data-stu-id="40e2b-107">Method</span></span>|<span data-ttu-id="40e2b-108">說明</span><span class="sxs-lookup"><span data-stu-id="40e2b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40e2b-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="40e2b-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="40e2b-110">擷取作業效能計數器執行個體名稱</span><span class="sxs-lookup"><span data-stu-id="40e2b-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="40e2b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="40e2b-111">Properties</span></span>  
 <span data-ttu-id="40e2b-112">Endpoint 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="40e2b-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="40e2b-113">地址</span><span class="sxs-lookup"><span data-stu-id="40e2b-113">Address</span></span>  
 <span data-ttu-id="40e2b-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="40e2b-114">Data type: string</span></span>  
  
 <span data-ttu-id="40e2b-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-116">包含端點位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="40e2b-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="40e2b-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="40e2b-117">AddressHeaders</span></span>  
 <span data-ttu-id="40e2b-118">資料型別：字串陣列</span><span class="sxs-lookup"><span data-stu-id="40e2b-118">Data type: string array</span></span>  
  
 <span data-ttu-id="40e2b-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-120">附加到此端點之位址標頭的集合。</span><span class="sxs-lookup"><span data-stu-id="40e2b-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="40e2b-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="40e2b-121">AddressIdentity</span></span>  
 <span data-ttu-id="40e2b-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="40e2b-122">Data type: string</span></span>  
  
 <span data-ttu-id="40e2b-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-124">端點的身分識別。</span><span class="sxs-lookup"><span data-stu-id="40e2b-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="40e2b-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="40e2b-125">AppDomainId</span></span>  
 <span data-ttu-id="40e2b-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="40e2b-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="40e2b-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-128">裝載端點之 appdomain 的 appdomain 識別碼。</span><span class="sxs-lookup"><span data-stu-id="40e2b-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="40e2b-129">行為</span><span class="sxs-lookup"><span data-stu-id="40e2b-129">Behaviors</span></span>  
 <span data-ttu-id="40e2b-130">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="40e2b-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="40e2b-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-132">此端點實作之行為的集合。</span><span class="sxs-lookup"><span data-stu-id="40e2b-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="40e2b-133">繫結</span><span class="sxs-lookup"><span data-stu-id="40e2b-133">Binding</span></span>  
 <span data-ttu-id="40e2b-134">資料型別：繫結</span><span class="sxs-lookup"><span data-stu-id="40e2b-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="40e2b-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-136">此端點所使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="40e2b-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="40e2b-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="40e2b-137">ContractName</span></span>  
 <span data-ttu-id="40e2b-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="40e2b-138">Data type: string</span></span>  
  
 <span data-ttu-id="40e2b-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-140">指定公開此端點之合約的字串。</span><span class="sxs-lookup"><span data-stu-id="40e2b-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="40e2b-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="40e2b-141">CounterInstanceName</span></span>  
 <span data-ttu-id="40e2b-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="40e2b-142">Data type: string</span></span>  
  
 <span data-ttu-id="40e2b-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-144">端點之效能計數器執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="40e2b-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="40e2b-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="40e2b-145">ListenUri</span></span>  
 <span data-ttu-id="40e2b-146">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="40e2b-146">Data type: string</span></span>  
  
 <span data-ttu-id="40e2b-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-148">端點接聽的 Uri。</span><span class="sxs-lookup"><span data-stu-id="40e2b-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="40e2b-149">名稱</span><span class="sxs-lookup"><span data-stu-id="40e2b-149">Name</span></span>  
 <span data-ttu-id="40e2b-150">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="40e2b-150">Data type: string</span></span>  
  
 <span data-ttu-id="40e2b-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-152">此端點的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="40e2b-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="40e2b-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="40e2b-153">ProcessId</span></span>  
 <span data-ttu-id="40e2b-154">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="40e2b-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="40e2b-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-156">裝載端點之處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="40e2b-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="40e2b-157">ref</span><span class="sxs-lookup"><span data-stu-id="40e2b-157">ref</span></span>  
 <span data-ttu-id="40e2b-158">資料型別：合約</span><span class="sxs-lookup"><span data-stu-id="40e2b-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="40e2b-159">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="40e2b-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40e2b-160">此端點公開的合約。</span><span class="sxs-lookup"><span data-stu-id="40e2b-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40e2b-161">需求</span><span class="sxs-lookup"><span data-stu-id="40e2b-161">Requirements</span></span>  
  
|<span data-ttu-id="40e2b-162">MOF</span><span class="sxs-lookup"><span data-stu-id="40e2b-162">MOF</span></span>|<span data-ttu-id="40e2b-163">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="40e2b-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="40e2b-164">命名空間</span><span class="sxs-lookup"><span data-stu-id="40e2b-164">Namespace</span></span>|<span data-ttu-id="40e2b-165">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="40e2b-165">Defined in root\ServiceModel</span></span>|
