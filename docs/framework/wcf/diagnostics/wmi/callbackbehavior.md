---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 9d8f4335c304d164daafeb0ad4de5b4e3bba4590
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963952"
---
# <a name="callbackbehavior"></a><span data-ttu-id="62e3d-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="62e3d-102">CallbackBehavior</span></span>
<span data-ttu-id="62e3d-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="62e3d-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="62e3d-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="62e3d-105">方法</span><span class="sxs-lookup"><span data-stu-id="62e3d-105">Methods</span></span>  
 <span data-ttu-id="62e3d-106">CallbackBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="62e3d-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="62e3d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="62e3d-107">Properties</span></span>  
 <span data-ttu-id="62e3d-108">CallbackBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="62e3d-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="62e3d-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="62e3d-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="62e3d-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="62e3d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="62e3d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62e3d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e3d-112">如果是 true，當服務關閉雙工工作階段時會自動關閉該工作階段。</span><span class="sxs-lookup"><span data-stu-id="62e3d-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="62e3d-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="62e3d-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="62e3d-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="62e3d-114">Data type: string</span></span>  
<span data-ttu-id="62e3d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62e3d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e3d-116">指定服務支援單一執行緒、多重執行緒或可重新進入 (Reentrant) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="62e3d-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="62e3d-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="62e3d-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="62e3d-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="62e3d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="62e3d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62e3d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e3d-120">指定是否要將未知的序列化資料傳送到網路上的值。</span><span class="sxs-lookup"><span data-stu-id="62e3d-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="62e3d-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="62e3d-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="62e3d-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="62e3d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="62e3d-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62e3d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e3d-124">啟用時，回呼上之例外狀況的詳細資料會附加到傳回到服務的錯誤中。</span><span class="sxs-lookup"><span data-stu-id="62e3d-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="62e3d-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="62e3d-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="62e3d-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="62e3d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="62e3d-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62e3d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e3d-128">已序列化物件中允許的項目數目上限。</span><span class="sxs-lookup"><span data-stu-id="62e3d-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="62e3d-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="62e3d-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="62e3d-130">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="62e3d-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="62e3d-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62e3d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e3d-132">指定是否使用目前的同步化內容來選擇執行的執行緒。</span><span class="sxs-lookup"><span data-stu-id="62e3d-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="62e3d-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="62e3d-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="62e3d-134">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="62e3d-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="62e3d-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="62e3d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62e3d-136">指定系統或應用程式是否會強制執行 SOAP MustUnderstand 標頭處理。</span><span class="sxs-lookup"><span data-stu-id="62e3d-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e3d-137">需求</span><span class="sxs-lookup"><span data-stu-id="62e3d-137">Requirements</span></span>  
  
|<span data-ttu-id="62e3d-138">MOF</span><span class="sxs-lookup"><span data-stu-id="62e3d-138">MOF</span></span>|<span data-ttu-id="62e3d-139">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="62e3d-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="62e3d-140">命名空間</span><span class="sxs-lookup"><span data-stu-id="62e3d-140">Namespace</span></span>|<span data-ttu-id="62e3d-141">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="62e3d-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62e3d-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62e3d-142">See also</span></span>

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
