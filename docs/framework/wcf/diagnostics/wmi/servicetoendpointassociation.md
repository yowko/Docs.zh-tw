---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 6e20556541b1aa48e7dfc6a8cde97e1bc477457e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273941"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="022ce-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="022ce-102">ServiceToEndpointAssociation</span></span>

<span data-ttu-id="022ce-103">將服務對應至端點。</span><span class="sxs-lookup"><span data-stu-id="022ce-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="022ce-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="022ce-104">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="022ce-105">方法</span><span class="sxs-lookup"><span data-stu-id="022ce-105">Methods</span></span>  

 <span data-ttu-id="022ce-106">ServiceToEndpointAssociation 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="022ce-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="022ce-107">屬性</span><span class="sxs-lookup"><span data-stu-id="022ce-107">Properties</span></span>  

 <span data-ttu-id="022ce-108">ServiceToEndpointAssociation 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="022ce-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="022ce-109">ref</span><span class="sxs-lookup"><span data-stu-id="022ce-109">ref</span></span>  

 <span data-ttu-id="022ce-110">資料型別：服務</span><span class="sxs-lookup"><span data-stu-id="022ce-110">Data type: Service</span></span>  
  
 <span data-ttu-id="022ce-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="022ce-111">Access type: Read-only</span></span>  
<span data-ttu-id="022ce-112">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="022ce-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="022ce-113">與端點關聯的服務。</span><span class="sxs-lookup"><span data-stu-id="022ce-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="022ce-114">ref</span><span class="sxs-lookup"><span data-stu-id="022ce-114">ref</span></span>  

 <span data-ttu-id="022ce-115">資料型別：端點</span><span class="sxs-lookup"><span data-stu-id="022ce-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="022ce-116">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="022ce-116">Access type: Read-only</span></span>  
<span data-ttu-id="022ce-117">限定詞：索引鍵</span><span class="sxs-lookup"><span data-stu-id="022ce-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="022ce-118">與服務關聯的端點。</span><span class="sxs-lookup"><span data-stu-id="022ce-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="022ce-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="022ce-119">Requirements</span></span>  
  
|<span data-ttu-id="022ce-120">MOF</span><span class="sxs-lookup"><span data-stu-id="022ce-120">MOF</span></span>|<span data-ttu-id="022ce-121">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="022ce-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="022ce-122">命名空間</span><span class="sxs-lookup"><span data-stu-id="022ce-122">Namespace</span></span>|<span data-ttu-id="022ce-123">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="022ce-123">Defined in root\ServiceModel</span></span>|
