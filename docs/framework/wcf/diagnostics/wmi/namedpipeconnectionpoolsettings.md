---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3dddfa878e3cb5bd89fb76009d0dba530debb297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725073"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="c590c-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c590c-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="c590c-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c590c-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c590c-104">語法</span><span class="sxs-lookup"><span data-stu-id="c590c-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c590c-105">方法</span><span class="sxs-lookup"><span data-stu-id="c590c-105">Methods</span></span>  
 <span data-ttu-id="c590c-106">NamedPipeConnectionPoolSettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="c590c-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c590c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c590c-107">Properties</span></span>  
 <span data-ttu-id="c590c-108">NamedPipeConnectionPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="c590c-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="c590c-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="c590c-109">GroupName</span></span>  
 <span data-ttu-id="c590c-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="c590c-110">Data type: string</span></span>  
  
 <span data-ttu-id="c590c-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c590c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c590c-112">繫結項目所使用之連線集區的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="c590c-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="c590c-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="c590c-113">IdleTimeout</span></span>  
 <span data-ttu-id="c590c-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="c590c-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="c590c-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c590c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c590c-116">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="c590c-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="c590c-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="c590c-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="c590c-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="c590c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c590c-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="c590c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c590c-120">用戶端上每個端點的傳出連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="c590c-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c590c-121">需求</span><span class="sxs-lookup"><span data-stu-id="c590c-121">Requirements</span></span>  
  
|<span data-ttu-id="c590c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c590c-122">MOF</span></span>|<span data-ttu-id="c590c-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="c590c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c590c-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="c590c-124">Namespace</span></span>|<span data-ttu-id="c590c-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="c590c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c590c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c590c-126">See also</span></span>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
