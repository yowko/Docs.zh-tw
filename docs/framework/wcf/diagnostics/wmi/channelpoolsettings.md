---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: d763be92243768bce9fdaefcd3e3575effac464b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200479"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="a3498-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a3498-102">ChannelPoolSettings</span></span>
<span data-ttu-id="a3498-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a3498-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3498-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3498-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a3498-105">方法</span><span class="sxs-lookup"><span data-stu-id="a3498-105">Methods</span></span>  
 <span data-ttu-id="a3498-106">ChannelPoolSettings 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a3498-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a3498-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a3498-107">Properties</span></span>  
 <span data-ttu-id="a3498-108">ChannelPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a3498-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="a3498-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a3498-109">IdleTimeout</span></span>  
 <span data-ttu-id="a3498-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="a3498-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="a3498-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a3498-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3498-112">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="a3498-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="a3498-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="a3498-113">LeaseTimeout</span></span>  
 <span data-ttu-id="a3498-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="a3498-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="a3498-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a3498-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3498-116">逾時前可完成租用作業的最長時間。</span><span class="sxs-lookup"><span data-stu-id="a3498-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="a3498-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="a3498-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="a3498-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="a3498-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="a3498-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a3498-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a3498-120">每個端點的傳出通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="a3498-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3498-121">需求</span><span class="sxs-lookup"><span data-stu-id="a3498-121">Requirements</span></span>  
  
|<span data-ttu-id="a3498-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a3498-122">MOF</span></span>|<span data-ttu-id="a3498-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a3498-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a3498-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="a3498-124">Namespace</span></span>|<span data-ttu-id="a3498-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a3498-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3498-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3498-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
