---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185179"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="bd612-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd612-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="bd612-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bd612-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd612-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd612-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bd612-105">方法</span><span class="sxs-lookup"><span data-stu-id="bd612-105">Methods</span></span>  
 <span data-ttu-id="bd612-106">PeerTransportBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="bd612-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bd612-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bd612-107">Properties</span></span>  
 <span data-ttu-id="bd612-108">PeerTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="bd612-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="bd612-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="bd612-109">ListenIPAddress</span></span>  
 <span data-ttu-id="bd612-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="bd612-110">Data type: string</span></span>  
  
 <span data-ttu-id="bd612-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bd612-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd612-112">對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="bd612-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="bd612-113">連接埠</span><span class="sxs-lookup"><span data-stu-id="bd612-113">Port</span></span>  
 <span data-ttu-id="bd612-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="bd612-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="bd612-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bd612-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd612-116">這個繫結處理對等通道 TCP 訊息所在的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="bd612-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="bd612-117">安全性</span><span class="sxs-lookup"><span data-stu-id="bd612-117">Security</span></span>  
 <span data-ttu-id="bd612-118">資料型別：PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="bd612-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="bd612-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bd612-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bd612-120">對應傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="bd612-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd612-121">需求</span><span class="sxs-lookup"><span data-stu-id="bd612-121">Requirements</span></span>  
  
|<span data-ttu-id="bd612-122">MOF</span><span class="sxs-lookup"><span data-stu-id="bd612-122">MOF</span></span>|<span data-ttu-id="bd612-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="bd612-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bd612-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="bd612-124">Namespace</span></span>|<span data-ttu-id="bd612-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="bd612-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd612-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd612-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
