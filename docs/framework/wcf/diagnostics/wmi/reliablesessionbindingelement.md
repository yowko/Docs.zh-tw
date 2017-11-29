---
title: ReliableSessionBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f4aff60c96db5071d41a3f011019b05746f0c96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="f61d5-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="f61d5-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="f61d5-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="f61d5-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f61d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="f61d5-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="f61d5-105">方法</span><span class="sxs-lookup"><span data-stu-id="f61d5-105">Methods</span></span>  
 <span data-ttu-id="f61d5-106">ReliableSessionBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f61d5-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f61d5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f61d5-107">Properties</span></span>  
 <span data-ttu-id="f61d5-108">ReliableSessionBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f61d5-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="f61d5-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="f61d5-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="f61d5-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f61d5-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="f61d5-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-112">目的地傳送確認到可靠通道 (由處理站所建立) 上的訊息來源之前等候的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f61d5-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="f61d5-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="f61d5-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="f61d5-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f61d5-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="f61d5-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-116">指定是否已啟用流量控制的布林值。</span><span class="sxs-lookup"><span data-stu-id="f61d5-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="f61d5-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="f61d5-117">InactivityTimeout</span></span>  
 <span data-ttu-id="f61d5-118">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f61d5-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="f61d5-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-120">指定將通道判定為失敗之前可允許另一個通訊方不傳送任何訊息的最長期間。</span><span class="sxs-lookup"><span data-stu-id="f61d5-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="f61d5-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="f61d5-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="f61d5-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f61d5-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="f61d5-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-124">可在接聽項上等候接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="f61d5-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="f61d5-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="f61d5-125">MaxRetryCount</span></span>  
 <span data-ttu-id="f61d5-126">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f61d5-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="f61d5-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-128">可靠通道透過在其基礎通道呼叫 `Send`，以嘗試重新傳輸尚未收到確認之訊息的最大次數。</span><span class="sxs-lookup"><span data-stu-id="f61d5-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="f61d5-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="f61d5-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="f61d5-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f61d5-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="f61d5-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-132">可靠工作階段的傳輸窗口大小上限。</span><span class="sxs-lookup"><span data-stu-id="f61d5-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="f61d5-133">Ordered</span><span class="sxs-lookup"><span data-stu-id="f61d5-133">Ordered</span></span>  
 <span data-ttu-id="f61d5-134">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f61d5-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="f61d5-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-136">布林值，指定是否保證訊息以傳送順序送達。</span><span class="sxs-lookup"><span data-stu-id="f61d5-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="f61d5-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="f61d5-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="f61d5-138">資料型別：整數</span><span class="sxs-lookup"><span data-stu-id="f61d5-138">Data type: integer</span></span>  
  
 <span data-ttu-id="f61d5-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f61d5-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f61d5-140">指定用於可靠工作階段中 WS-ReliableMessaging 通訊協定版本的整數。</span><span class="sxs-lookup"><span data-stu-id="f61d5-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f61d5-141">需求</span><span class="sxs-lookup"><span data-stu-id="f61d5-141">Requirements</span></span>  
  
|<span data-ttu-id="f61d5-142">MOF</span><span class="sxs-lookup"><span data-stu-id="f61d5-142">MOF</span></span>|<span data-ttu-id="f61d5-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f61d5-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f61d5-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="f61d5-144">Namespace</span></span>|<span data-ttu-id="f61d5-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f61d5-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f61d5-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f61d5-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
