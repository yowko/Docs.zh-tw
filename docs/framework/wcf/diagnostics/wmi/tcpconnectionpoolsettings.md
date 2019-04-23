---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975337"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="a58d2-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a58d2-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="a58d2-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a58d2-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58d2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a58d2-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a58d2-105">方法</span><span class="sxs-lookup"><span data-stu-id="a58d2-105">Methods</span></span>  
 <span data-ttu-id="a58d2-106">TcpConnectionPoolSettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a58d2-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a58d2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a58d2-107">Properties</span></span>  
 <span data-ttu-id="a58d2-108">TcpConnectionPoolSettings 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a58d2-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="a58d2-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="a58d2-109">GroupName</span></span>  
 <span data-ttu-id="a58d2-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a58d2-110">Data type: string</span></span>  
  
 <span data-ttu-id="a58d2-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a58d2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a58d2-112">繫結項目所使用之連線集區的群組名稱。</span><span class="sxs-lookup"><span data-stu-id="a58d2-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="a58d2-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a58d2-113">IdleTimeout</span></span>  
 <span data-ttu-id="a58d2-114">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="a58d2-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="a58d2-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a58d2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a58d2-116">連線中斷之前可閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="a58d2-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="a58d2-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="a58d2-117">LeaseTimeout</span></span>  
 <span data-ttu-id="a58d2-118">資料型別：日期時間</span><span class="sxs-lookup"><span data-stu-id="a58d2-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="a58d2-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a58d2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a58d2-120">逾時前可完成租用作業的最長時間。</span><span class="sxs-lookup"><span data-stu-id="a58d2-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="a58d2-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="a58d2-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="a58d2-122">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="a58d2-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="a58d2-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a58d2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a58d2-124">每個端點的傳出連線數目上限。</span><span class="sxs-lookup"><span data-stu-id="a58d2-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58d2-125">需求</span><span class="sxs-lookup"><span data-stu-id="a58d2-125">Requirements</span></span>  
  
|<span data-ttu-id="a58d2-126">MOF</span><span class="sxs-lookup"><span data-stu-id="a58d2-126">MOF</span></span>|<span data-ttu-id="a58d2-127">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a58d2-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a58d2-128">命名空間</span><span class="sxs-lookup"><span data-stu-id="a58d2-128">Namespace</span></span>|<span data-ttu-id="a58d2-129">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a58d2-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a58d2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a58d2-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
