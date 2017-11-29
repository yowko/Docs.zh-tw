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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf9c39334289cb30d1a01917c0be37da02fcdc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="9064d-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9064d-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="9064d-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9064d-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9064d-104">語法</span><span class="sxs-lookup"><span data-stu-id="9064d-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9064d-105">方法</span><span class="sxs-lookup"><span data-stu-id="9064d-105">Methods</span></span>  
 <span data-ttu-id="9064d-106">NamedPipeConnectionPoolSettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="9064d-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9064d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9064d-107">Properties</span></span>  
 <span data-ttu-id="9064d-108">NamedPipeConnectionPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="9064d-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="9064d-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="9064d-109">GroupName</span></span>  
 <span data-ttu-id="9064d-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="9064d-110">Data type: string</span></span>  
  
 <span data-ttu-id="9064d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9064d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9064d-112">繫結項目所使用之連線集區的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="9064d-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="9064d-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="9064d-113">IdleTimeout</span></span>  
 <span data-ttu-id="9064d-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="9064d-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="9064d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9064d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9064d-116">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="9064d-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="9064d-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="9064d-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="9064d-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="9064d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="9064d-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="9064d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9064d-120">用戶端上每個端點的傳出連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="9064d-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9064d-121">需求</span><span class="sxs-lookup"><span data-stu-id="9064d-121">Requirements</span></span>  
  
|<span data-ttu-id="9064d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="9064d-122">MOF</span></span>|<span data-ttu-id="9064d-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="9064d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9064d-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="9064d-124">Namespace</span></span>|<span data-ttu-id="9064d-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="9064d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9064d-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9064d-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
