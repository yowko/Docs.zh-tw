---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963968"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="cee16-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cee16-102">ChannelPoolSettings</span></span>
<span data-ttu-id="cee16-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cee16-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cee16-104">語法</span><span class="sxs-lookup"><span data-stu-id="cee16-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cee16-105">方法</span><span class="sxs-lookup"><span data-stu-id="cee16-105">Methods</span></span>  
 <span data-ttu-id="cee16-106">ChannelPoolSettings 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="cee16-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cee16-107">屬性</span><span class="sxs-lookup"><span data-stu-id="cee16-107">Properties</span></span>  
 <span data-ttu-id="cee16-108">ChannelPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="cee16-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="cee16-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="cee16-109">IdleTimeout</span></span>  
 <span data-ttu-id="cee16-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="cee16-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="cee16-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="cee16-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cee16-112">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="cee16-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="cee16-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="cee16-113">LeaseTimeout</span></span>  
 <span data-ttu-id="cee16-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="cee16-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="cee16-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="cee16-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cee16-116">逾時前可完成租用作業的最長時間。</span><span class="sxs-lookup"><span data-stu-id="cee16-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="cee16-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="cee16-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="cee16-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="cee16-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="cee16-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="cee16-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cee16-120">每個端點的傳出通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="cee16-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cee16-121">需求</span><span class="sxs-lookup"><span data-stu-id="cee16-121">Requirements</span></span>  
  
|<span data-ttu-id="cee16-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cee16-122">MOF</span></span>|<span data-ttu-id="cee16-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="cee16-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cee16-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="cee16-124">Namespace</span></span>|<span data-ttu-id="cee16-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="cee16-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cee16-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cee16-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
