---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195810"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="fcb3a-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="fcb3a-102">OneWayBindingElement</span></span>
<span data-ttu-id="fcb3a-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="fcb3a-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcb3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcb3a-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fcb3a-105">方法</span><span class="sxs-lookup"><span data-stu-id="fcb3a-105">Methods</span></span>  
 <span data-ttu-id="fcb3a-106">OneWayBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="fcb3a-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fcb3a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fcb3a-107">Properties</span></span>  
 <span data-ttu-id="fcb3a-108">OneWayBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="fcb3a-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="fcb3a-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="fcb3a-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="fcb3a-110">資料型別：ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="fcb3a-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="fcb3a-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fcb3a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fcb3a-112">通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="fcb3a-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="fcb3a-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="fcb3a-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="fcb3a-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="fcb3a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="fcb3a-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fcb3a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fcb3a-116">已接受之通道的數目上限。</span><span class="sxs-lookup"><span data-stu-id="fcb3a-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="fcb3a-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="fcb3a-117">PacketRoutable</span></span>  
 <span data-ttu-id="fcb3a-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="fcb3a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="fcb3a-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="fcb3a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fcb3a-120">代表封包是否為可路由傳送的值。</span><span class="sxs-lookup"><span data-stu-id="fcb3a-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcb3a-121">需求</span><span class="sxs-lookup"><span data-stu-id="fcb3a-121">Requirements</span></span>  
  
|<span data-ttu-id="fcb3a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="fcb3a-122">MOF</span></span>|<span data-ttu-id="fcb3a-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="fcb3a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fcb3a-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="fcb3a-124">Namespace</span></span>|<span data-ttu-id="fcb3a-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="fcb3a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcb3a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb3a-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
