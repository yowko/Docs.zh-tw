---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979234"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="1cece-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="1cece-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="1cece-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="1cece-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cece-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cece-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1cece-105">方法</span><span class="sxs-lookup"><span data-stu-id="1cece-105">Methods</span></span>  
 <span data-ttu-id="1cece-106">TcpTransportBindingElement 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="1cece-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1cece-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1cece-107">Properties</span></span>  
 <span data-ttu-id="1cece-108">TcpTransportBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1cece-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="1cece-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="1cece-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="1cece-110">資料類型：TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="1cece-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="1cece-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1cece-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1cece-112">連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="1cece-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="1cece-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="1cece-113">ListenBacklog</span></span>  
 <span data-ttu-id="1cece-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="1cece-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1cece-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1cece-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1cece-116">可以擱置之佇列連線要求的最大數目。</span><span class="sxs-lookup"><span data-stu-id="1cece-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="1cece-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="1cece-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="1cece-118">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="1cece-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1cece-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1cece-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1cece-120">布林值，這個值指定是否為此連線啟用 TCP 連接埠共用。</span><span class="sxs-lookup"><span data-stu-id="1cece-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="1cece-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="1cece-121">TeredoEnabled</span></span>  
 <span data-ttu-id="1cece-122">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="1cece-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1cece-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1cece-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1cece-124">布林值，指定是否啟用 Teredo (對防火牆後的用戶端進行定址的技術)。</span><span class="sxs-lookup"><span data-stu-id="1cece-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cece-125">需求</span><span class="sxs-lookup"><span data-stu-id="1cece-125">Requirements</span></span>  
  
|<span data-ttu-id="1cece-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1cece-126">MOF</span></span>|<span data-ttu-id="1cece-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="1cece-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1cece-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="1cece-128">Namespace</span></span>|<span data-ttu-id="1cece-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="1cece-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1cece-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cece-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
