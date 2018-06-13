---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485641"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="16e58-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="16e58-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="16e58-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="16e58-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e58-104">語法</span><span class="sxs-lookup"><span data-stu-id="16e58-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="16e58-105">方法</span><span class="sxs-lookup"><span data-stu-id="16e58-105">Methods</span></span>  
 <span data-ttu-id="16e58-106">PeerTransportBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="16e58-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="16e58-107">屬性</span><span class="sxs-lookup"><span data-stu-id="16e58-107">Properties</span></span>  
 <span data-ttu-id="16e58-108">PeerTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="16e58-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="16e58-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="16e58-109">ListenIPAddress</span></span>  
 <span data-ttu-id="16e58-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="16e58-110">Data type: string</span></span>  
  
 <span data-ttu-id="16e58-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="16e58-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16e58-112">對等節點接聽 TCP 訊息的 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="16e58-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="16e58-113">連接埠</span><span class="sxs-lookup"><span data-stu-id="16e58-113">Port</span></span>  
 <span data-ttu-id="16e58-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="16e58-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="16e58-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="16e58-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16e58-116">這個繫結處理對等通道 TCP 訊息所在的網路介面連接埠。</span><span class="sxs-lookup"><span data-stu-id="16e58-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="16e58-117">安全性</span><span class="sxs-lookup"><span data-stu-id="16e58-117">Security</span></span>  
 <span data-ttu-id="16e58-118">資料型別：PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="16e58-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="16e58-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="16e58-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16e58-120">對應傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="16e58-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16e58-121">需求</span><span class="sxs-lookup"><span data-stu-id="16e58-121">Requirements</span></span>  
  
|<span data-ttu-id="16e58-122">MOF</span><span class="sxs-lookup"><span data-stu-id="16e58-122">MOF</span></span>|<span data-ttu-id="16e58-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="16e58-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="16e58-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="16e58-124">Namespace</span></span>|<span data-ttu-id="16e58-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="16e58-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16e58-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16e58-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
