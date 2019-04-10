---
title: 支援查詢
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 30695fcd791a0d69c31a897068d69838c80c3957
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307947"
---
# <a name="support-for-queries"></a><span data-ttu-id="ef786-102">支援查詢</span><span class="sxs-lookup"><span data-stu-id="ef786-102">Support for Queries</span></span>
<span data-ttu-id="ef786-103">SQL 工作流程執行個體存放區會記錄存放區中一組已知的屬性。</span><span class="sxs-lookup"><span data-stu-id="ef786-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="ef786-104">使用者可以根據這些屬性查詢執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef786-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="ef786-105">下列清單包含其中一些已知的屬性：</span><span class="sxs-lookup"><span data-stu-id="ef786-105">The following list contains some of these well-known properties:</span></span>  
  
-   **<span data-ttu-id="ef786-106">網站名稱：</span><span class="sxs-lookup"><span data-stu-id="ef786-106">Site Name.</span></span>** <span data-ttu-id="ef786-107">包含服務之網站的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef786-107">Name of the Web site that contains the service.</span></span>  
  
-   **<span data-ttu-id="ef786-108">相對應用程式路徑：</span><span class="sxs-lookup"><span data-stu-id="ef786-108">Relative Application Path.</span></span>** <span data-ttu-id="ef786-109">應用程式的路徑 (相對於網站)。</span><span class="sxs-lookup"><span data-stu-id="ef786-109">Path of the application relative to the Web site.</span></span>  
  
-   **<span data-ttu-id="ef786-110">相對服務路徑：</span><span class="sxs-lookup"><span data-stu-id="ef786-110">Relative Service Path.</span></span>** <span data-ttu-id="ef786-111">服務的路徑 (相對於應用程式)。</span><span class="sxs-lookup"><span data-stu-id="ef786-111">Path of the service relative to the application.</span></span>  
  
-   **<span data-ttu-id="ef786-112">服務名稱：</span><span class="sxs-lookup"><span data-stu-id="ef786-112">Service Name.</span></span>** <span data-ttu-id="ef786-113">服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef786-113">Name of the service.</span></span>  
  
-   **<span data-ttu-id="ef786-114">服務命名空間：</span><span class="sxs-lookup"><span data-stu-id="ef786-114">Service Namespace.</span></span>** <span data-ttu-id="ef786-115">服務所使用之命名空間的名稱。</span><span class="sxs-lookup"><span data-stu-id="ef786-115">Name of the namespace that the service uses.</span></span>  
  
-   **<span data-ttu-id="ef786-116">目前的電腦：</span><span class="sxs-lookup"><span data-stu-id="ef786-116">Current Machine.</span></span>**  
  
-   <span data-ttu-id="ef786-117">**上次的電腦**。</span><span class="sxs-lookup"><span data-stu-id="ef786-117">**Last Machine**.</span></span> <span data-ttu-id="ef786-118">工作流程服務執行個體上一次執行所在的電腦。</span><span class="sxs-lookup"><span data-stu-id="ef786-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef786-119">若為使用工作流程服務主機的自我裝載案例，只會填入後四個屬性。</span><span class="sxs-lookup"><span data-stu-id="ef786-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="ef786-120">若為工作流程應用程式案例，則只會填入最後一個屬性。</span><span class="sxs-lookup"><span data-stu-id="ef786-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="ef786-121">工作流程執行階段會提供前三個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ef786-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="ef786-122">工作流程服務主機提供的值**暫止原因**屬性。</span><span class="sxs-lookup"><span data-stu-id="ef786-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="ef786-123">SQL 工作流程執行個體存放區本身提供的值**上次更新的電腦**屬性。</span><span class="sxs-lookup"><span data-stu-id="ef786-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="ef786-124">SQL 工作流程執行個體存放區功能亦可讓您指定自訂屬性 (您可以將這些屬性的值存放在持續性資料庫中以及用於查詢中)。</span><span class="sxs-lookup"><span data-stu-id="ef786-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="ef786-125">如需自訂提升的詳細資訊，請參閱[存放區擴充性](store-extensibility.md)。</span><span class="sxs-lookup"><span data-stu-id="ef786-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="ef786-126">檢視</span><span class="sxs-lookup"><span data-stu-id="ef786-126">Views</span></span>  
 <span data-ttu-id="ef786-127">執行個體存放區包含下列檢視。</span><span class="sxs-lookup"><span data-stu-id="ef786-127">The instance store contains the following views.</span></span> <span data-ttu-id="ef786-128">請參閱[持續性資料庫結構描述](persistence-database-schema.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ef786-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="ef786-129">Instances 檢視表</span><span class="sxs-lookup"><span data-stu-id="ef786-129">The Instances View</span></span>  
 <span data-ttu-id="ef786-130">Instances 檢視表包含下列欄位：</span><span class="sxs-lookup"><span data-stu-id="ef786-130">The Instances view contains the following fields:</span></span>  
  
1. **<span data-ttu-id="ef786-131">ID</span><span class="sxs-lookup"><span data-stu-id="ef786-131">Id</span></span>**  
  
2. **<span data-ttu-id="ef786-132">PendingTimer</span><span class="sxs-lookup"><span data-stu-id="ef786-132">PendingTimer</span></span>**  
  
3. **<span data-ttu-id="ef786-133">CreationTime</span><span class="sxs-lookup"><span data-stu-id="ef786-133">CreationTime</span></span>**  
  
4. **<span data-ttu-id="ef786-134">LastUpdatedTime</span><span class="sxs-lookup"><span data-stu-id="ef786-134">LastUpdatedTime</span></span>**  
  
5. **<span data-ttu-id="ef786-135">ServiceDeploymentId</span><span class="sxs-lookup"><span data-stu-id="ef786-135">ServiceDeploymentId</span></span>**  
  
6. **<span data-ttu-id="ef786-136">SuspensionExceptionName</span><span class="sxs-lookup"><span data-stu-id="ef786-136">SuspensionExceptionName</span></span>**  
  
7. **<span data-ttu-id="ef786-137">SuspensionReason</span><span class="sxs-lookup"><span data-stu-id="ef786-137">SuspensionReason</span></span>**  
  
8. **<span data-ttu-id="ef786-138">ActiveBookmarks</span><span class="sxs-lookup"><span data-stu-id="ef786-138">ActiveBookmarks</span></span>**  
  
9. **<span data-ttu-id="ef786-139">CurrentMachine</span><span class="sxs-lookup"><span data-stu-id="ef786-139">CurrentMachine</span></span>**  
  
10. **<span data-ttu-id="ef786-140">LastMachine</span><span class="sxs-lookup"><span data-stu-id="ef786-140">LastMachine</span></span>**  
  
11. **<span data-ttu-id="ef786-141">ExecutionStatus</span><span class="sxs-lookup"><span data-stu-id="ef786-141">ExecutionStatus</span></span>**  
  
12. **<span data-ttu-id="ef786-142">IsInitialized</span><span class="sxs-lookup"><span data-stu-id="ef786-142">IsInitialized</span></span>**  
  
13. **<span data-ttu-id="ef786-143">IsSuspended</span><span class="sxs-lookup"><span data-stu-id="ef786-143">IsSuspended</span></span>**  
  
14. **<span data-ttu-id="ef786-144">IsCompleted</span><span class="sxs-lookup"><span data-stu-id="ef786-144">IsCompleted</span></span>**  
  
15. **<span data-ttu-id="ef786-145">EncodingOption</span><span class="sxs-lookup"><span data-stu-id="ef786-145">EncodingOption</span></span>**  
  
16. **<span data-ttu-id="ef786-146">ReadWritePrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="ef786-146">ReadWritePrimitiveDataProperties</span></span>**  
  
17. **<span data-ttu-id="ef786-147">WriteOnlyPrimitiveDataProperties</span><span class="sxs-lookup"><span data-stu-id="ef786-147">WriteOnlyPrimitiveDataProperties</span></span>**  
  
18. **<span data-ttu-id="ef786-148">ReadWriteComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="ef786-148">ReadWriteComplexDataProperties</span></span>**  
  
19. **<span data-ttu-id="ef786-149">WriteOnlyComplexDataProperties</span><span class="sxs-lookup"><span data-stu-id="ef786-149">WriteOnlyComplexDataProperties</span></span>**  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="ef786-150">ServiceDeployments 檢視表</span><span class="sxs-lookup"><span data-stu-id="ef786-150">The ServiceDeployments view</span></span>  
 <span data-ttu-id="ef786-151">ServiceDeployments 檢視表包含下列欄位：</span><span class="sxs-lookup"><span data-stu-id="ef786-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. **<span data-ttu-id="ef786-152">SiteName</span><span class="sxs-lookup"><span data-stu-id="ef786-152">SiteName</span></span>**  
  
2. **<span data-ttu-id="ef786-153">RelativeServicePath</span><span class="sxs-lookup"><span data-stu-id="ef786-153">RelativeServicePath</span></span>**  
  
3. **<span data-ttu-id="ef786-154">RelativeApplicationPath</span><span class="sxs-lookup"><span data-stu-id="ef786-154">RelativeApplicationPath</span></span>**  
  
4. **<span data-ttu-id="ef786-155">ServiceName</span><span class="sxs-lookup"><span data-stu-id="ef786-155">ServiceName</span></span>**  
  
5. **<span data-ttu-id="ef786-156">ServiceNamespace</span><span class="sxs-lookup"><span data-stu-id="ef786-156">ServiceNamespace</span></span>**  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="ef786-157">InstancePromotedProperties 檢視表</span><span class="sxs-lookup"><span data-stu-id="ef786-157">The InstancePromotedProperties view</span></span>  
 <span data-ttu-id="ef786-158">InstancePromotedProperties 檢視表包含下列欄位。</span><span class="sxs-lookup"><span data-stu-id="ef786-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="ef786-159">如需提升之屬性的詳細資訊，請參閱[存放區擴充性](store-extensibility.md)主題。</span><span class="sxs-lookup"><span data-stu-id="ef786-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. **<span data-ttu-id="ef786-160">InstanceId</span><span class="sxs-lookup"><span data-stu-id="ef786-160">InstanceId</span></span>**  
  
2. **<span data-ttu-id="ef786-161">EncodingOption</span><span class="sxs-lookup"><span data-stu-id="ef786-161">EncodingOption</span></span>**  
  
3. **<span data-ttu-id="ef786-162">PromotionName</span><span class="sxs-lookup"><span data-stu-id="ef786-162">PromotionName</span></span>**  
  
4. <span data-ttu-id="ef786-163">**Value #** (範圍中的欄位**Value1**要**Value64**)。</span><span class="sxs-lookup"><span data-stu-id="ef786-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
