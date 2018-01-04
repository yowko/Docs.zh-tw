---
title: ServiceBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6b0620e9cb2575bcfe9cd6f01b5d87669df69b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="14bfe-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="14bfe-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="14bfe-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="14bfe-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14bfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="14bfe-104">Syntax</span></span>  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="14bfe-105">方法</span><span class="sxs-lookup"><span data-stu-id="14bfe-105">Methods</span></span>  
 <span data-ttu-id="14bfe-106">ServiceBehaviorAttribute 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="14bfe-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="14bfe-107">屬性</span><span class="sxs-lookup"><span data-stu-id="14bfe-107">Properties</span></span>  
 <span data-ttu-id="14bfe-108">ServiceBehaviorAttribute 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="14bfe-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="14bfe-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="14bfe-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="14bfe-110">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="14bfe-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="14bfe-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-112">代表是否要在用戶端關閉輸出工作階段時自動關閉工作階段。</span><span class="sxs-lookup"><span data-stu-id="14bfe-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="14bfe-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="14bfe-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="14bfe-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="14bfe-114">Data type: string</span></span>  
<span data-ttu-id="14bfe-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-116">代表服務支援單一執行緒、多重執行緒或可重新進入 (Reentrant) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="14bfe-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="14bfe-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="14bfe-117">ConfigurationName</span></span>  
 <span data-ttu-id="14bfe-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="14bfe-118">Data type: string</span></span>  
  
 <span data-ttu-id="14bfe-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-120">服務組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="14bfe-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="14bfe-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="14bfe-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="14bfe-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="14bfe-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="14bfe-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-124">指定是否要將未知的序列化資料傳送到網路上的值。</span><span class="sxs-lookup"><span data-stu-id="14bfe-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="14bfe-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="14bfe-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="14bfe-126">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="14bfe-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="14bfe-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-128">指定是否要針對偵錯用途，在傳回給用戶端的 SOAP 錯誤詳細資料中包含 Managed 例外狀況資訊。</span><span class="sxs-lookup"><span data-stu-id="14bfe-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="14bfe-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="14bfe-129">InstanceContextMode</span></span>  
 <span data-ttu-id="14bfe-130">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="14bfe-130">Data type: string</span></span>  
  
 <span data-ttu-id="14bfe-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-132">指定何時建立新的服務物件。</span><span class="sxs-lookup"><span data-stu-id="14bfe-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="14bfe-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="14bfe-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="14bfe-134">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="14bfe-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="14bfe-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-136">已序列化物件中允許的項目數目上限。</span><span class="sxs-lookup"><span data-stu-id="14bfe-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="14bfe-137">名稱</span><span class="sxs-lookup"><span data-stu-id="14bfe-137">Name</span></span>  
 <span data-ttu-id="14bfe-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="14bfe-138">Data type: string</span></span>  
  
 <span data-ttu-id="14bfe-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-140">WSDL 格式的服務名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="14bfe-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="14bfe-141">命名空間</span><span class="sxs-lookup"><span data-stu-id="14bfe-141">Namespace</span></span>  
 <span data-ttu-id="14bfe-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="14bfe-142">Data type: string</span></span>  
  
 <span data-ttu-id="14bfe-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-144">WSDL 格式的服務目標命名空間。</span><span class="sxs-lookup"><span data-stu-id="14bfe-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="14bfe-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="14bfe-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="14bfe-146">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="14bfe-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="14bfe-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-148">指定是否會在目前的交易完成時回收服務物件。</span><span class="sxs-lookup"><span data-stu-id="14bfe-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="14bfe-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="14bfe-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="14bfe-150">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="14bfe-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="14bfe-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-152">指定當目前的工作階段關閉時，是否會完成暫止的異動。</span><span class="sxs-lookup"><span data-stu-id="14bfe-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="14bfe-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="14bfe-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="14bfe-154">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="14bfe-154">Data type: string</span></span>  
  
 <span data-ttu-id="14bfe-155">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-156">指定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="14bfe-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="14bfe-157">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="14bfe-157">TransactionTimeout</span></span>  
 <span data-ttu-id="14bfe-158">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="14bfe-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="14bfe-159">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-160">異動必須完成的期間。</span><span class="sxs-lookup"><span data-stu-id="14bfe-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="14bfe-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="14bfe-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="14bfe-162">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="14bfe-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="14bfe-163">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-164">指定是否使用目前的同步化內容來選擇執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="14bfe-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="14bfe-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="14bfe-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="14bfe-166">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="14bfe-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="14bfe-167">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="14bfe-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14bfe-168">指定系統或應用程式是否會強制執行 SOAP MustUnderstand 標頭處理。</span><span class="sxs-lookup"><span data-stu-id="14bfe-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14bfe-169">需求</span><span class="sxs-lookup"><span data-stu-id="14bfe-169">Requirements</span></span>  
  
|<span data-ttu-id="14bfe-170">MOF</span><span class="sxs-lookup"><span data-stu-id="14bfe-170">MOF</span></span>|<span data-ttu-id="14bfe-171">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="14bfe-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="14bfe-172">命名空間</span><span class="sxs-lookup"><span data-stu-id="14bfe-172">Namespace</span></span>|<span data-ttu-id="14bfe-173">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="14bfe-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14bfe-174">請參閱</span><span class="sxs-lookup"><span data-stu-id="14bfe-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
