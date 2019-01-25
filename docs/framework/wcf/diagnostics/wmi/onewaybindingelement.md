---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: d84184febd6db3f233aae6fe558b8e0f50a9cb82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608832"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="307c3-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="307c3-102">OneWayBindingElement</span></span>
<span data-ttu-id="307c3-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="307c3-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="307c3-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="307c3-105">方法</span><span class="sxs-lookup"><span data-stu-id="307c3-105">Methods</span></span>  
 <span data-ttu-id="307c3-106">OneWayBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="307c3-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="307c3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="307c3-107">Properties</span></span>  
 <span data-ttu-id="307c3-108">OneWayBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="307c3-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="307c3-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="307c3-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="307c3-110">資料類型：ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="307c3-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="307c3-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="307c3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307c3-112">通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="307c3-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="307c3-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="307c3-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="307c3-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="307c3-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="307c3-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="307c3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307c3-116">已接受之通道的數目上限。</span><span class="sxs-lookup"><span data-stu-id="307c3-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="307c3-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="307c3-117">PacketRoutable</span></span>  
 <span data-ttu-id="307c3-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="307c3-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="307c3-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="307c3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="307c3-120">代表封包是否為可路由傳送的值。</span><span class="sxs-lookup"><span data-stu-id="307c3-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="307c3-121">需求</span><span class="sxs-lookup"><span data-stu-id="307c3-121">Requirements</span></span>  
  
|<span data-ttu-id="307c3-122">MOF</span><span class="sxs-lookup"><span data-stu-id="307c3-122">MOF</span></span>|<span data-ttu-id="307c3-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="307c3-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="307c3-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="307c3-124">Namespace</span></span>|<span data-ttu-id="307c3-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="307c3-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="307c3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="307c3-126">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement>
