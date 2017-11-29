---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="af1d6-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="af1d6-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="af1d6-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="af1d6-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af1d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="af1d6-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="af1d6-105">方法</span><span class="sxs-lookup"><span data-stu-id="af1d6-105">Methods</span></span>  
 <span data-ttu-id="af1d6-106">PeerTransportBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="af1d6-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="af1d6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="af1d6-107">Properties</span></span>  
 <span data-ttu-id="af1d6-108">PeerTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="af1d6-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="af1d6-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="af1d6-109">ListenIPAddress</span></span>  
 <span data-ttu-id="af1d6-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="af1d6-110">Data type: string</span></span>  
  
 <span data-ttu-id="af1d6-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="af1d6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af1d6-112">對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="af1d6-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="af1d6-113">通訊埠</span><span class="sxs-lookup"><span data-stu-id="af1d6-113">Port</span></span>  
 <span data-ttu-id="af1d6-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="af1d6-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="af1d6-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="af1d6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af1d6-116">這個繫結處理對等通道 TCP 訊息所在的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="af1d6-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="af1d6-117">安全性</span><span class="sxs-lookup"><span data-stu-id="af1d6-117">Security</span></span>  
 <span data-ttu-id="af1d6-118">資料型別：PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="af1d6-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="af1d6-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="af1d6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af1d6-120">對應傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="af1d6-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af1d6-121">需求</span><span class="sxs-lookup"><span data-stu-id="af1d6-121">Requirements</span></span>  
  
|<span data-ttu-id="af1d6-122">MOF</span><span class="sxs-lookup"><span data-stu-id="af1d6-122">MOF</span></span>|<span data-ttu-id="af1d6-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="af1d6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="af1d6-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="af1d6-124">Namespace</span></span>|<span data-ttu-id="af1d6-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="af1d6-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af1d6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af1d6-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
