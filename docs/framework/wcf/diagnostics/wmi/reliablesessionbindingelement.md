---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: b0a621da43402777cc620f1876bd968a72bb8c12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962912"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="dba4b-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="dba4b-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="dba4b-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="dba4b-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="dba4b-104">Syntax</span></span>  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dba4b-105">方法</span><span class="sxs-lookup"><span data-stu-id="dba4b-105">Methods</span></span>  
 <span data-ttu-id="dba4b-106">ReliableSessionBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="dba4b-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dba4b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="dba4b-107">Properties</span></span>  
 <span data-ttu-id="dba4b-108">ReliableSessionBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="dba4b-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="dba4b-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="dba4b-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="dba4b-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="dba4b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="dba4b-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-112">目的地傳送確認到可靠通道 (由處理站所建立) 上的訊息來源之前等候的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="dba4b-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="dba4b-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="dba4b-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="dba4b-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="dba4b-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="dba4b-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-116">指定是否已啟用流量控制的布林值。</span><span class="sxs-lookup"><span data-stu-id="dba4b-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="dba4b-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="dba4b-117">InactivityTimeout</span></span>  
 <span data-ttu-id="dba4b-118">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="dba4b-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="dba4b-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-120">指定將通道判定為失敗之前可允許另一個通訊方不傳送任何訊息的最長期間。</span><span class="sxs-lookup"><span data-stu-id="dba4b-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="dba4b-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="dba4b-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="dba4b-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="dba4b-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="dba4b-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-124">可在接聽項上等候接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="dba4b-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="dba4b-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="dba4b-125">MaxRetryCount</span></span>  
 <span data-ttu-id="dba4b-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="dba4b-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="dba4b-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-128">可靠通道透過在其基礎通道呼叫 `Send`，以嘗試重新傳輸尚未收到確認之訊息的最大次數。</span><span class="sxs-lookup"><span data-stu-id="dba4b-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="dba4b-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="dba4b-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="dba4b-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="dba4b-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="dba4b-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-132">可靠工作階段的傳輸窗口大小上限。</span><span class="sxs-lookup"><span data-stu-id="dba4b-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="dba4b-133">排序</span><span class="sxs-lookup"><span data-stu-id="dba4b-133">Ordered</span></span>  
 <span data-ttu-id="dba4b-134">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="dba4b-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="dba4b-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-136">布林值，指定是否保證訊息以傳送順序送達。</span><span class="sxs-lookup"><span data-stu-id="dba4b-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="dba4b-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="dba4b-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="dba4b-138">資料型別：整數</span><span class="sxs-lookup"><span data-stu-id="dba4b-138">Data type: integer</span></span>  
  
 <span data-ttu-id="dba4b-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dba4b-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dba4b-140">指定用於可靠工作階段中 WS-ReliableMessaging 通訊協定版本的整數。</span><span class="sxs-lookup"><span data-stu-id="dba4b-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba4b-141">需求</span><span class="sxs-lookup"><span data-stu-id="dba4b-141">Requirements</span></span>  
  
|<span data-ttu-id="dba4b-142">MOF</span><span class="sxs-lookup"><span data-stu-id="dba4b-142">MOF</span></span>|<span data-ttu-id="dba4b-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="dba4b-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dba4b-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="dba4b-144">Namespace</span></span>|<span data-ttu-id="dba4b-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="dba4b-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dba4b-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba4b-146">See also</span></span>

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
