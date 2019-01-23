---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 4a3e45140765f99f4a30b77fc9d02b167601b50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591470"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="ed395-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ed395-102">ChannelPoolSettings</span></span>
<span data-ttu-id="ed395-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="ed395-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed395-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed395-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ed395-105">方法</span><span class="sxs-lookup"><span data-stu-id="ed395-105">Methods</span></span>  
 <span data-ttu-id="ed395-106">ChannelPoolSettings 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="ed395-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ed395-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ed395-107">Properties</span></span>  
 <span data-ttu-id="ed395-108">ChannelPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="ed395-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="ed395-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="ed395-109">IdleTimeout</span></span>  
 <span data-ttu-id="ed395-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="ed395-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="ed395-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ed395-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ed395-112">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="ed395-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="ed395-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="ed395-113">LeaseTimeout</span></span>  
 <span data-ttu-id="ed395-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="ed395-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="ed395-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ed395-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ed395-116">逾時前可完成租用作業的最長時間。</span><span class="sxs-lookup"><span data-stu-id="ed395-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="ed395-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="ed395-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="ed395-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="ed395-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="ed395-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ed395-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ed395-120">每個端點的傳出通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="ed395-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed395-121">需求</span><span class="sxs-lookup"><span data-stu-id="ed395-121">Requirements</span></span>  
  
|<span data-ttu-id="ed395-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ed395-122">MOF</span></span>|<span data-ttu-id="ed395-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="ed395-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ed395-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="ed395-124">Namespace</span></span>|<span data-ttu-id="ed395-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="ed395-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed395-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed395-126">See also</span></span>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
