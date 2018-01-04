---
title: NamedPipeConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 601ccd5589da759606365570538e0df902e4fbe2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="f59fa-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f59fa-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="f59fa-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f59fa-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f59fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="f59fa-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f59fa-105">方法</span><span class="sxs-lookup"><span data-stu-id="f59fa-105">Methods</span></span>  
 <span data-ttu-id="f59fa-106">NamedPipeConnectionPoolSettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f59fa-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f59fa-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f59fa-107">Properties</span></span>  
 <span data-ttu-id="f59fa-108">NamedPipeConnectionPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f59fa-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="f59fa-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="f59fa-109">GroupName</span></span>  
 <span data-ttu-id="f59fa-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f59fa-110">Data type: string</span></span>  
  
 <span data-ttu-id="f59fa-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f59fa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f59fa-112">繫結項目所使用之連線集區的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="f59fa-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="f59fa-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="f59fa-113">IdleTimeout</span></span>  
 <span data-ttu-id="f59fa-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="f59fa-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="f59fa-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f59fa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f59fa-116">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="f59fa-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="f59fa-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="f59fa-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="f59fa-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="f59fa-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f59fa-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f59fa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f59fa-120">用戶端上每個端點的傳出連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="f59fa-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f59fa-121">需求</span><span class="sxs-lookup"><span data-stu-id="f59fa-121">Requirements</span></span>  
  
|<span data-ttu-id="f59fa-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f59fa-122">MOF</span></span>|<span data-ttu-id="f59fa-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f59fa-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f59fa-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="f59fa-124">Namespace</span></span>|<span data-ttu-id="f59fa-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f59fa-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f59fa-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="f59fa-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
