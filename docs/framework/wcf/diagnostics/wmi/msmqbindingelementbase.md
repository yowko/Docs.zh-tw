---
title: MsmqBindingElementBase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10e476931ef07ec694dff200e64ce2ded74c8dfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="f2237-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="f2237-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="f2237-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="f2237-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2237-104">語法</span><span class="sxs-lookup"><span data-stu-id="f2237-104">Syntax</span></span>  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f2237-105">方法</span><span class="sxs-lookup"><span data-stu-id="f2237-105">Methods</span></span>  
 <span data-ttu-id="f2237-106">MsmqBindingElementBase 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f2237-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f2237-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f2237-107">Properties</span></span>  
 <span data-ttu-id="f2237-108">MsmqBindingElementBase 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f2237-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="f2237-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="f2237-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="f2237-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f2237-110">Data type: string</span></span>  
  
 <span data-ttu-id="f2237-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-112">包含每個應用程式寄不出的信件佇列位置的 URI，該佇列含有已過期、無法傳輸或延遲傳遞的訊息。</span><span class="sxs-lookup"><span data-stu-id="f2237-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="f2237-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="f2237-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="f2237-114">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f2237-114">Data type: string</span></span>  
  
 <span data-ttu-id="f2237-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-116">代表要使用之寄不出的信件佇列類型的列舉值。</span><span class="sxs-lookup"><span data-stu-id="f2237-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="f2237-117">Durable</span><span class="sxs-lookup"><span data-stu-id="f2237-117">Durable</span></span>  
 <span data-ttu-id="f2237-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f2237-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2237-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-120">代表此繫結處理之訊息為永久性或變動性的值。</span><span class="sxs-lookup"><span data-stu-id="f2237-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="f2237-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="f2237-121">ExactlyOnce</span></span>  
 <span data-ttu-id="f2237-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f2237-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2237-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-124">代表由此繫結處理的訊息是否只接收一次的布林值。</span><span class="sxs-lookup"><span data-stu-id="f2237-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="f2237-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="f2237-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="f2237-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f2237-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="f2237-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-128">嘗試傳遞訊息至接收應用程式的重試循環次數上限。</span><span class="sxs-lookup"><span data-stu-id="f2237-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="f2237-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="f2237-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="f2237-130">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f2237-130">Data type: string</span></span>  
  
 <span data-ttu-id="f2237-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-132">有害訊息處理設定。</span><span class="sxs-lookup"><span data-stu-id="f2237-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="f2237-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="f2237-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="f2237-134">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f2237-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="f2237-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-136">從應用程式佇列讀取之訊息的立即重試次數上限。</span><span class="sxs-lookup"><span data-stu-id="f2237-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="f2237-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="f2237-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="f2237-138">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f2237-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2237-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-140">代表嘗試傳遞無法立即傳遞之訊息時，重試循環之間的時間延遲值。</span><span class="sxs-lookup"><span data-stu-id="f2237-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="f2237-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="f2237-141">TimeToLive</span></span>  
 <span data-ttu-id="f2237-142">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f2237-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2237-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-144">代表由此繫結所處理之訊息在到期前可保留在佇列中的時間間隔值。</span><span class="sxs-lookup"><span data-stu-id="f2237-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="f2237-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="f2237-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="f2237-146">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f2237-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2237-147">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-148">代表是否應該追蹤由此繫結所處理之訊息的布林值。</span><span class="sxs-lookup"><span data-stu-id="f2237-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="f2237-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="f2237-149">UseSourceJournal</span></span>  
 <span data-ttu-id="f2237-150">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f2237-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2237-151">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f2237-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2237-152">代表由此繫結所處理之訊息複本是否應該儲存在來源日誌佇列的布林值。</span><span class="sxs-lookup"><span data-stu-id="f2237-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2237-153">需求</span><span class="sxs-lookup"><span data-stu-id="f2237-153">Requirements</span></span>  
  
|<span data-ttu-id="f2237-154">MOF</span><span class="sxs-lookup"><span data-stu-id="f2237-154">MOF</span></span>|<span data-ttu-id="f2237-155">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f2237-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f2237-156">命名空間</span><span class="sxs-lookup"><span data-stu-id="f2237-156">Namespace</span></span>|<span data-ttu-id="f2237-157">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f2237-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2237-158">請參閱</span><span class="sxs-lookup"><span data-stu-id="f2237-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
