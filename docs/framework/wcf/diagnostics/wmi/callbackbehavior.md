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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9df9629e280a2aec6acf93773e09384e763280ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="c1efb-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="c1efb-102">CallbackBehavior</span></span>
<span data-ttu-id="c1efb-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="c1efb-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1efb-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1efb-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="c1efb-105">方法</span><span class="sxs-lookup"><span data-stu-id="c1efb-105">Methods</span></span>  
 <span data-ttu-id="c1efb-106">CallbackBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="c1efb-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c1efb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c1efb-107">Properties</span></span>  
 <span data-ttu-id="c1efb-108">CallbackBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="c1efb-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="c1efb-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="c1efb-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="c1efb-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="c1efb-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1efb-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c1efb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1efb-112">如果是 true，當服務關閉雙工工作階段時會自動關閉該工作階段。</span><span class="sxs-lookup"><span data-stu-id="c1efb-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="c1efb-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="c1efb-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="c1efb-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="c1efb-114">Data type: string</span></span>  
<span data-ttu-id="c1efb-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c1efb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1efb-116">指定服務支援單一執行緒、多重執行緒或可重新進入 (Reentrant) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="c1efb-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="c1efb-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c1efb-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="c1efb-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="c1efb-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1efb-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c1efb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1efb-120">指定是否要將未知的序列化資料傳送到網路上的值。</span><span class="sxs-lookup"><span data-stu-id="c1efb-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="c1efb-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="c1efb-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="c1efb-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="c1efb-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1efb-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c1efb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1efb-124">啟用時，回呼上之例外狀況的詳細資料會附加到傳回到服務的錯誤中。</span><span class="sxs-lookup"><span data-stu-id="c1efb-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="c1efb-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c1efb-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="c1efb-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="c1efb-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1efb-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c1efb-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1efb-128">已序列化物件中允許的項目數目上限。</span><span class="sxs-lookup"><span data-stu-id="c1efb-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="c1efb-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="c1efb-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="c1efb-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="c1efb-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1efb-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c1efb-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1efb-132">指定是否使用目前的同步化內容來選擇執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c1efb-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="c1efb-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="c1efb-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="c1efb-134">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="c1efb-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1efb-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c1efb-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1efb-136">指定系統或應用程式是否會強制執行 SOAP MustUnderstand 標頭處理。</span><span class="sxs-lookup"><span data-stu-id="c1efb-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1efb-137">需求</span><span class="sxs-lookup"><span data-stu-id="c1efb-137">Requirements</span></span>  
  
|<span data-ttu-id="c1efb-138">MOF</span><span class="sxs-lookup"><span data-stu-id="c1efb-138">MOF</span></span>|<span data-ttu-id="c1efb-139">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="c1efb-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c1efb-140">命名空間</span><span class="sxs-lookup"><span data-stu-id="c1efb-140">Namespace</span></span>|<span data-ttu-id="c1efb-141">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="c1efb-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1efb-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1efb-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
