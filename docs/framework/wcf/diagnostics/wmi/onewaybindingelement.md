---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="af574-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="af574-102">OneWayBindingElement</span></span>
<span data-ttu-id="af574-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="af574-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af574-104">語法</span><span class="sxs-lookup"><span data-stu-id="af574-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="af574-105">方法</span><span class="sxs-lookup"><span data-stu-id="af574-105">Methods</span></span>  
 <span data-ttu-id="af574-106">OneWayBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="af574-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="af574-107">屬性</span><span class="sxs-lookup"><span data-stu-id="af574-107">Properties</span></span>  
 <span data-ttu-id="af574-108">OneWayBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="af574-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="af574-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="af574-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="af574-110">資料型別：ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="af574-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="af574-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="af574-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af574-112">通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="af574-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="af574-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="af574-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="af574-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="af574-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="af574-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="af574-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af574-116">已接受之通道的數目上限。</span><span class="sxs-lookup"><span data-stu-id="af574-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="af574-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="af574-117">PacketRoutable</span></span>  
 <span data-ttu-id="af574-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="af574-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="af574-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="af574-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af574-120">代表封包是否為可路由傳送的值。</span><span class="sxs-lookup"><span data-stu-id="af574-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af574-121">需求</span><span class="sxs-lookup"><span data-stu-id="af574-121">Requirements</span></span>  
  
|<span data-ttu-id="af574-122">MOF</span><span class="sxs-lookup"><span data-stu-id="af574-122">MOF</span></span>|<span data-ttu-id="af574-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="af574-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="af574-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="af574-124">Namespace</span></span>|<span data-ttu-id="af574-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="af574-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af574-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="af574-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
