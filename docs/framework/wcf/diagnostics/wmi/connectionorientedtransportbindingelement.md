---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 49f030c05f02280d483ac2a836cbe75716b7b5cc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185050"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="dfc6d-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dfc6d-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="dfc6d-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="dfc6d-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc6d-104">語法</span><span class="sxs-lookup"><span data-stu-id="dfc6d-104">Syntax</span></span>  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dfc6d-105">方法</span><span class="sxs-lookup"><span data-stu-id="dfc6d-105">Methods</span></span>  
 <span data-ttu-id="dfc6d-106">ConnectionOrientedTransportBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dfc6d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="dfc6d-107">Properties</span></span>  
 <span data-ttu-id="dfc6d-108">ConnectionOrientedTransportBindingElement 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="dfc6d-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="dfc6d-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="dfc6d-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="dfc6d-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="dfc6d-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="dfc6d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-112">指定在逾時之前必須完成通道初始化的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="dfc6d-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="dfc6d-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="dfc6d-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="dfc6d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="dfc6d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-116">用於從用戶端或服務在網路上傳輸已序列化訊息之區塊的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="dfc6d-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="dfc6d-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="dfc6d-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="dfc6d-118">Data type: string</span></span>  
  
 <span data-ttu-id="dfc6d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-120">代表主機名稱是否用於連線到服務的值 (當符合 URI 時)。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="dfc6d-121">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="dfc6d-121">MaxBufferSize</span></span>  
 <span data-ttu-id="dfc6d-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="dfc6d-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="dfc6d-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-124">要使用之緩衝區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="dfc6d-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="dfc6d-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="dfc6d-126">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="dfc6d-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="dfc6d-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-128">訊息區塊或完整訊息在送出之前，可以在記憶體中保持緩衝的最大時間間隔。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="dfc6d-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="dfc6d-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="dfc6d-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="dfc6d-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="dfc6d-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-132">可用來處理服務之連入連線的擱置中非同步接受執行緒數目上限。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="dfc6d-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="dfc6d-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="dfc6d-134">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="dfc6d-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="dfc6d-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-136">服務的擱置連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="dfc6d-137">TransferMode</span><span class="sxs-lookup"><span data-stu-id="dfc6d-137">TransferMode</span></span>  
 <span data-ttu-id="dfc6d-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="dfc6d-138">Data type: string</span></span>  
  
 <span data-ttu-id="dfc6d-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="dfc6d-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dfc6d-140">指定訊息是否使用連線導向傳輸進行緩衝或資料流處理的值。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc6d-141">需求</span><span class="sxs-lookup"><span data-stu-id="dfc6d-141">Requirements</span></span>  
  
|<span data-ttu-id="dfc6d-142">MOF</span><span class="sxs-lookup"><span data-stu-id="dfc6d-142">MOF</span></span>|<span data-ttu-id="dfc6d-143">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="dfc6d-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dfc6d-144">命名空間</span><span class="sxs-lookup"><span data-stu-id="dfc6d-144">Namespace</span></span>|<span data-ttu-id="dfc6d-145">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="dfc6d-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dfc6d-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfc6d-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
