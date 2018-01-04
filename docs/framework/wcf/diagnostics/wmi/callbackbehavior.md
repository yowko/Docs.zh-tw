---
title: CallbackBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5387e197cdf26a393ba23fd5696eb095dfd17a70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="4e833-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="4e833-102">CallbackBehavior</span></span>
<span data-ttu-id="4e833-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="4e833-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e833-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e833-104">Syntax</span></span>  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4e833-105">方法</span><span class="sxs-lookup"><span data-stu-id="4e833-105">Methods</span></span>  
 <span data-ttu-id="4e833-106">CallbackBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="4e833-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4e833-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4e833-107">Properties</span></span>  
 <span data-ttu-id="4e833-108">CallbackBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4e833-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="4e833-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="4e833-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="4e833-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="4e833-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e833-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4e833-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e833-112">如果是 true，當服務關閉雙工工作階段時會自動關閉該工作階段。</span><span class="sxs-lookup"><span data-stu-id="4e833-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="4e833-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="4e833-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="4e833-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="4e833-114">Data type: string</span></span>  
<span data-ttu-id="4e833-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4e833-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e833-116">指定服務支援單一執行緒、多重執行緒或可重新進入 (Reentrant) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="4e833-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="4e833-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="4e833-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="4e833-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="4e833-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e833-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4e833-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e833-120">指定是否要將未知的序列化資料傳送到網路上的值。</span><span class="sxs-lookup"><span data-stu-id="4e833-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="4e833-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="4e833-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="4e833-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="4e833-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e833-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4e833-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e833-124">啟用時，回呼上之例外狀況的詳細資料會附加到傳回到服務的錯誤中。</span><span class="sxs-lookup"><span data-stu-id="4e833-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="4e833-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="4e833-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="4e833-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="4e833-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e833-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4e833-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e833-128">已序列化物件中允許的項目數目上限。</span><span class="sxs-lookup"><span data-stu-id="4e833-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="4e833-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="4e833-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="4e833-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="4e833-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e833-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4e833-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e833-132">指定是否使用目前的同步化內容來選擇執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="4e833-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="4e833-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="4e833-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="4e833-134">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="4e833-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e833-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="4e833-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e833-136">指定系統或應用程式是否會強制執行 SOAP MustUnderstand 標頭處理。</span><span class="sxs-lookup"><span data-stu-id="4e833-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e833-137">需求</span><span class="sxs-lookup"><span data-stu-id="4e833-137">Requirements</span></span>  
  
|<span data-ttu-id="4e833-138">MOF</span><span class="sxs-lookup"><span data-stu-id="4e833-138">MOF</span></span>|<span data-ttu-id="4e833-139">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="4e833-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4e833-140">命名空間</span><span class="sxs-lookup"><span data-stu-id="4e833-140">Namespace</span></span>|<span data-ttu-id="4e833-141">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="4e833-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e833-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="4e833-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
