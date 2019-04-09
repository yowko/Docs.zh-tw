---
title: Channel 類別
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128839"
---
# <a name="channel-class"></a><span data-ttu-id="5eb53-102">Channel 類別</span><span class="sxs-lookup"><span data-stu-id="5eb53-102">Channel class</span></span>
<span data-ttu-id="5eb53-103">通道</span><span class="sxs-lookup"><span data-stu-id="5eb53-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5eb53-104">語法</span><span class="sxs-lookup"><span data-stu-id="5eb53-104">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5eb53-105">方法</span><span class="sxs-lookup"><span data-stu-id="5eb53-105">Methods</span></span>  
 <span data-ttu-id="5eb53-106">Channel 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="5eb53-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5eb53-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5eb53-107">Properties</span></span>  
 <span data-ttu-id="5eb53-108">Channel 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="5eb53-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="5eb53-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="5eb53-109">LocalAddress</span></span>  
 <span data-ttu-id="5eb53-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="5eb53-110">Data type: string</span></span>  
  
 <span data-ttu-id="5eb53-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5eb53-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5eb53-112">通道的本機端點。</span><span class="sxs-lookup"><span data-stu-id="5eb53-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="5eb53-113">ref</span><span class="sxs-lookup"><span data-stu-id="5eb53-113">ref</span></span>  
 <span data-ttu-id="5eb53-114">資料類型：端點</span><span class="sxs-lookup"><span data-stu-id="5eb53-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="5eb53-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5eb53-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5eb53-116">通道所連接之端點的參考。</span><span class="sxs-lookup"><span data-stu-id="5eb53-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="5eb53-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="5eb53-117">RemoteAddress</span></span>  
 <span data-ttu-id="5eb53-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="5eb53-118">Data type: string</span></span>  
  
 <span data-ttu-id="5eb53-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5eb53-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5eb53-120">與通道相關聯的遠端位址。</span><span class="sxs-lookup"><span data-stu-id="5eb53-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="5eb53-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="5eb53-121">SessionId</span></span>  
 <span data-ttu-id="5eb53-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="5eb53-122">Data type: string</span></span>  
  
 <span data-ttu-id="5eb53-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5eb53-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5eb53-124">目前工作階段識別碼 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="5eb53-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="5eb53-125">類型</span><span class="sxs-lookup"><span data-stu-id="5eb53-125">Type</span></span>  
 <span data-ttu-id="5eb53-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="5eb53-126">Data type: string</span></span>  
  
 <span data-ttu-id="5eb53-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="5eb53-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5eb53-128">通道的類型。</span><span class="sxs-lookup"><span data-stu-id="5eb53-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5eb53-129">需求</span><span class="sxs-lookup"><span data-stu-id="5eb53-129">Requirements</span></span>  
  
|<span data-ttu-id="5eb53-130">MOF</span><span class="sxs-lookup"><span data-stu-id="5eb53-130">MOF</span></span>|<span data-ttu-id="5eb53-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="5eb53-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5eb53-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="5eb53-132">Namespace</span></span>|<span data-ttu-id="5eb53-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="5eb53-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5eb53-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eb53-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
