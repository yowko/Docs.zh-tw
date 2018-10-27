---
title: Channel 類別
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50047367"
---
# <a name="channel-class"></a><span data-ttu-id="63dae-102">Channel 類別</span><span class="sxs-lookup"><span data-stu-id="63dae-102">Channel class</span></span>
<span data-ttu-id="63dae-103">通道</span><span class="sxs-lookup"><span data-stu-id="63dae-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63dae-104">語法</span><span class="sxs-lookup"><span data-stu-id="63dae-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="63dae-105">方法</span><span class="sxs-lookup"><span data-stu-id="63dae-105">Methods</span></span>  
 <span data-ttu-id="63dae-106">Channel 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="63dae-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="63dae-107">屬性</span><span class="sxs-lookup"><span data-stu-id="63dae-107">Properties</span></span>  
 <span data-ttu-id="63dae-108">Channel 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="63dae-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="63dae-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="63dae-109">LocalAddress</span></span>  
 <span data-ttu-id="63dae-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63dae-110">Data type: string</span></span>  
  
 <span data-ttu-id="63dae-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63dae-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63dae-112">通道的本機端點。</span><span class="sxs-lookup"><span data-stu-id="63dae-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="63dae-113">ref</span><span class="sxs-lookup"><span data-stu-id="63dae-113">ref</span></span>  
 <span data-ttu-id="63dae-114">資料型別：端點</span><span class="sxs-lookup"><span data-stu-id="63dae-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="63dae-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63dae-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63dae-116">通道所連接之端點的參考。</span><span class="sxs-lookup"><span data-stu-id="63dae-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="63dae-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="63dae-117">RemoteAddress</span></span>  
 <span data-ttu-id="63dae-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63dae-118">Data type: string</span></span>  
  
 <span data-ttu-id="63dae-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63dae-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63dae-120">與通道相關聯的遠端位址。</span><span class="sxs-lookup"><span data-stu-id="63dae-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="63dae-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="63dae-121">SessionId</span></span>  
 <span data-ttu-id="63dae-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63dae-122">Data type: string</span></span>  
  
 <span data-ttu-id="63dae-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63dae-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63dae-124">目前工作階段識別碼 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="63dae-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="63dae-125">類型</span><span class="sxs-lookup"><span data-stu-id="63dae-125">Type</span></span>  
 <span data-ttu-id="63dae-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="63dae-126">Data type: string</span></span>  
  
 <span data-ttu-id="63dae-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="63dae-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="63dae-128">通道的類型。</span><span class="sxs-lookup"><span data-stu-id="63dae-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63dae-129">需求</span><span class="sxs-lookup"><span data-stu-id="63dae-129">Requirements</span></span>  
  
|<span data-ttu-id="63dae-130">MOF</span><span class="sxs-lookup"><span data-stu-id="63dae-130">MOF</span></span>|<span data-ttu-id="63dae-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="63dae-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="63dae-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="63dae-132">Namespace</span></span>|<span data-ttu-id="63dae-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="63dae-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63dae-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63dae-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
