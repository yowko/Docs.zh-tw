---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ae6a3448896cb206bce8867daf7104c3e484ecc8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269011"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="0033c-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0033c-102">PeerTransportBindingElement</span></span>

<span data-ttu-id="0033c-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0033c-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0033c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0033c-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0033c-105">方法</span><span class="sxs-lookup"><span data-stu-id="0033c-105">Methods</span></span>  

 <span data-ttu-id="0033c-106">PeerTransportBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="0033c-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0033c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0033c-107">Properties</span></span>  

 <span data-ttu-id="0033c-108">PeerTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0033c-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="0033c-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="0033c-109">ListenIPAddress</span></span>  

 <span data-ttu-id="0033c-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="0033c-110">Data type: string</span></span>  
  
 <span data-ttu-id="0033c-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0033c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0033c-112">對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="0033c-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="0033c-113">連接埠</span><span class="sxs-lookup"><span data-stu-id="0033c-113">Port</span></span>  

 <span data-ttu-id="0033c-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="0033c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="0033c-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0033c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0033c-116">這個繫結處理對等通道 TCP 訊息所在的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="0033c-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="0033c-117">安全性</span><span class="sxs-lookup"><span data-stu-id="0033c-117">Security</span></span>  

 <span data-ttu-id="0033c-118">資料型別：PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="0033c-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="0033c-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="0033c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0033c-120">對應傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0033c-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0033c-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="0033c-121">Requirements</span></span>  
  
|<span data-ttu-id="0033c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="0033c-122">MOF</span></span>|<span data-ttu-id="0033c-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="0033c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0033c-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="0033c-124">Namespace</span></span>|<span data-ttu-id="0033c-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="0033c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0033c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0033c-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
