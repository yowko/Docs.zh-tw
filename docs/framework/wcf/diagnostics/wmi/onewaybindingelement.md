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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43707f25a9ee1beb1ce7adac36a2c4a55cab6d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="7d37f-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="7d37f-102">OneWayBindingElement</span></span>
<span data-ttu-id="7d37f-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="7d37f-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d37f-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d37f-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7d37f-105">方法</span><span class="sxs-lookup"><span data-stu-id="7d37f-105">Methods</span></span>  
 <span data-ttu-id="7d37f-106">OneWayBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="7d37f-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7d37f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7d37f-107">Properties</span></span>  
 <span data-ttu-id="7d37f-108">OneWayBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7d37f-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="7d37f-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7d37f-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="7d37f-110">資料型別：ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7d37f-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="7d37f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7d37f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d37f-112">通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="7d37f-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="7d37f-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="7d37f-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="7d37f-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="7d37f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="7d37f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7d37f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d37f-116">已接受之通道的數目上限。</span><span class="sxs-lookup"><span data-stu-id="7d37f-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="7d37f-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="7d37f-117">PacketRoutable</span></span>  
 <span data-ttu-id="7d37f-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="7d37f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="7d37f-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="7d37f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7d37f-120">代表封包是否為可路由傳送的值。</span><span class="sxs-lookup"><span data-stu-id="7d37f-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d37f-121">需求</span><span class="sxs-lookup"><span data-stu-id="7d37f-121">Requirements</span></span>  
  
|<span data-ttu-id="7d37f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7d37f-122">MOF</span></span>|<span data-ttu-id="7d37f-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="7d37f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7d37f-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="7d37f-124">Namespace</span></span>|<span data-ttu-id="7d37f-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="7d37f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d37f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d37f-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
