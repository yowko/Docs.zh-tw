---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 2de417e4a4f5c6197551c1408da6907e2fa7c635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268998"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="42d84-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="42d84-102">PeerSecuritySettings</span></span>

<span data-ttu-id="42d84-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="42d84-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42d84-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="42d84-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="42d84-105">方法</span><span class="sxs-lookup"><span data-stu-id="42d84-105">Methods</span></span>  

 <span data-ttu-id="42d84-106">PeerSecuritySettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="42d84-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="42d84-107">屬性</span><span class="sxs-lookup"><span data-stu-id="42d84-107">Properties</span></span>  

 <span data-ttu-id="42d84-108">PeerSecuritySettings 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="42d84-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="42d84-109">[模式]</span><span class="sxs-lookup"><span data-stu-id="42d84-109">Mode</span></span>  

 <span data-ttu-id="42d84-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="42d84-110">Data type: string</span></span>  
  
 <span data-ttu-id="42d84-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="42d84-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42d84-112">使用繫結設定之端點是否採用訊息層級與傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="42d84-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="42d84-113">傳輸</span><span class="sxs-lookup"><span data-stu-id="42d84-113">Transport</span></span>  

 <span data-ttu-id="42d84-114">資料型別：PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="42d84-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="42d84-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="42d84-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42d84-116">傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="42d84-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42d84-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="42d84-117">Requirements</span></span>  
  
|<span data-ttu-id="42d84-118">MOF</span><span class="sxs-lookup"><span data-stu-id="42d84-118">MOF</span></span>|<span data-ttu-id="42d84-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="42d84-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="42d84-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="42d84-120">Namespace</span></span>|<span data-ttu-id="42d84-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="42d84-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42d84-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42d84-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
