---
title: "Channel 類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1df634a61cce695fca74fdfe53beea6c0f83d082
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="channel-class"></a><span data-ttu-id="15a87-102">Channel 類別</span><span class="sxs-lookup"><span data-stu-id="15a87-102">Channel class</span></span>
<span data-ttu-id="15a87-103">通道</span><span class="sxs-lookup"><span data-stu-id="15a87-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15a87-104">語法</span><span class="sxs-lookup"><span data-stu-id="15a87-104">Syntax</span></span>  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="15a87-105">方法</span><span class="sxs-lookup"><span data-stu-id="15a87-105">Methods</span></span>  
 <span data-ttu-id="15a87-106">Channel 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="15a87-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="15a87-107">屬性</span><span class="sxs-lookup"><span data-stu-id="15a87-107">Properties</span></span>  
 <span data-ttu-id="15a87-108">Channel 類別具有下列屬性。</span><span class="sxs-lookup"><span data-stu-id="15a87-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="15a87-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="15a87-109">LocalAddress</span></span>  
 <span data-ttu-id="15a87-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="15a87-110">Data type: string</span></span>  
  
 <span data-ttu-id="15a87-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15a87-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15a87-112">通道的本機端點。</span><span class="sxs-lookup"><span data-stu-id="15a87-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="15a87-113">ref</span><span class="sxs-lookup"><span data-stu-id="15a87-113">ref</span></span>  
 <span data-ttu-id="15a87-114">資料型別：端點</span><span class="sxs-lookup"><span data-stu-id="15a87-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="15a87-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15a87-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15a87-116">通道所連接之端點的參考。</span><span class="sxs-lookup"><span data-stu-id="15a87-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="15a87-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="15a87-117">RemoteAddress</span></span>  
 <span data-ttu-id="15a87-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="15a87-118">Data type: string</span></span>  
  
 <span data-ttu-id="15a87-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15a87-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15a87-120">與通道相關聯的遠端位址。</span><span class="sxs-lookup"><span data-stu-id="15a87-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="15a87-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="15a87-121">SessionId</span></span>  
 <span data-ttu-id="15a87-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="15a87-122">Data type: string</span></span>  
  
 <span data-ttu-id="15a87-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15a87-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15a87-124">目前工作階段識別碼 (如果有)。</span><span class="sxs-lookup"><span data-stu-id="15a87-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="15a87-125">類型</span><span class="sxs-lookup"><span data-stu-id="15a87-125">Type</span></span>  
 <span data-ttu-id="15a87-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="15a87-126">Data type: string</span></span>  
  
 <span data-ttu-id="15a87-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="15a87-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="15a87-128">通道的類型。</span><span class="sxs-lookup"><span data-stu-id="15a87-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a87-129">需求</span><span class="sxs-lookup"><span data-stu-id="15a87-129">Requirements</span></span>  
  
|<span data-ttu-id="15a87-130">MOF</span><span class="sxs-lookup"><span data-stu-id="15a87-130">MOF</span></span>|<span data-ttu-id="15a87-131">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="15a87-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="15a87-132">命名空間</span><span class="sxs-lookup"><span data-stu-id="15a87-132">Namespace</span></span>|<span data-ttu-id="15a87-133">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="15a87-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15a87-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15a87-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
