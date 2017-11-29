---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 180e954661319cb32edfd3180418fe9b1571ea5c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="f0520-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f0520-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="f0520-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f0520-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0520-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0520-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f0520-105">方法</span><span class="sxs-lookup"><span data-stu-id="f0520-105">Methods</span></span>  
 <span data-ttu-id="f0520-106">TcpTransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f0520-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f0520-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f0520-107">Properties</span></span>  
 <span data-ttu-id="f0520-108">TcpTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f0520-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="f0520-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f0520-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="f0520-110">資料型別：TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f0520-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="f0520-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f0520-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0520-112">連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="f0520-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="f0520-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="f0520-113">ListenBacklog</span></span>  
 <span data-ttu-id="f0520-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f0520-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0520-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f0520-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0520-116">可以擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="f0520-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="f0520-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="f0520-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="f0520-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f0520-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f0520-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f0520-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0520-120">布林值，這個值指定是否為此連線啟用 TCP 連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="f0520-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="f0520-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="f0520-121">TeredoEnabled</span></span>  
 <span data-ttu-id="f0520-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="f0520-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f0520-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f0520-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0520-124">布林值，指定是否啟用 Teredo (對防火牆後的用戶端進行定址的技術)。</span><span class="sxs-lookup"><span data-stu-id="f0520-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0520-125">需求</span><span class="sxs-lookup"><span data-stu-id="f0520-125">Requirements</span></span>  
  
|<span data-ttu-id="f0520-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f0520-126">MOF</span></span>|<span data-ttu-id="f0520-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f0520-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f0520-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="f0520-128">Namespace</span></span>|<span data-ttu-id="f0520-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f0520-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0520-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0520-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
