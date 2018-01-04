---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3995b517b27a5565f7fcb9c11da27c9e1bb40887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="49e92-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="49e92-102">ChannelPoolSettings</span></span>
<span data-ttu-id="49e92-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="49e92-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e92-104">語法</span><span class="sxs-lookup"><span data-stu-id="49e92-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="49e92-105">方法</span><span class="sxs-lookup"><span data-stu-id="49e92-105">Methods</span></span>  
 <span data-ttu-id="49e92-106">ChannelPoolSettings 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="49e92-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="49e92-107">屬性</span><span class="sxs-lookup"><span data-stu-id="49e92-107">Properties</span></span>  
 <span data-ttu-id="49e92-108">ChannelPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="49e92-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="49e92-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="49e92-109">IdleTimeout</span></span>  
 <span data-ttu-id="49e92-110">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="49e92-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="49e92-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="49e92-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49e92-112">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="49e92-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="49e92-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="49e92-113">LeaseTimeout</span></span>  
 <span data-ttu-id="49e92-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="49e92-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="49e92-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="49e92-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49e92-116">逾時前可完成租用作業的最長時間。</span><span class="sxs-lookup"><span data-stu-id="49e92-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="49e92-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="49e92-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="49e92-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="49e92-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="49e92-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="49e92-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49e92-120">每個端點的傳出通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="49e92-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49e92-121">需求</span><span class="sxs-lookup"><span data-stu-id="49e92-121">Requirements</span></span>  
  
|<span data-ttu-id="49e92-122">MOF</span><span class="sxs-lookup"><span data-stu-id="49e92-122">MOF</span></span>|<span data-ttu-id="49e92-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="49e92-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="49e92-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="49e92-124">Namespace</span></span>|<span data-ttu-id="49e92-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="49e92-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49e92-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="49e92-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
