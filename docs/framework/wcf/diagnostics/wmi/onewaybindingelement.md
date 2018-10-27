---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50049291"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="e5eab-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5eab-102">OneWayBindingElement</span></span>
<span data-ttu-id="e5eab-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5eab-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5eab-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5eab-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e5eab-105">方法</span><span class="sxs-lookup"><span data-stu-id="e5eab-105">Methods</span></span>  
 <span data-ttu-id="e5eab-106">OneWayBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="e5eab-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e5eab-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e5eab-107">Properties</span></span>  
 <span data-ttu-id="e5eab-108">OneWayBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e5eab-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="e5eab-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e5eab-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="e5eab-110">資料型別：ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e5eab-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="e5eab-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e5eab-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5eab-112">通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="e5eab-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="e5eab-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="e5eab-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="e5eab-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="e5eab-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5eab-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e5eab-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5eab-116">已接受之通道的數目上限。</span><span class="sxs-lookup"><span data-stu-id="e5eab-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="e5eab-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="e5eab-117">PacketRoutable</span></span>  
 <span data-ttu-id="e5eab-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="e5eab-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e5eab-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e5eab-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5eab-120">代表封包是否為可路由傳送的值。</span><span class="sxs-lookup"><span data-stu-id="e5eab-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5eab-121">需求</span><span class="sxs-lookup"><span data-stu-id="e5eab-121">Requirements</span></span>  
  
|<span data-ttu-id="e5eab-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e5eab-122">MOF</span></span>|<span data-ttu-id="e5eab-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="e5eab-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e5eab-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="e5eab-124">Namespace</span></span>|<span data-ttu-id="e5eab-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="e5eab-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5eab-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5eab-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
