---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963003"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="ff49d-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ff49d-102">PeerSecuritySettings</span></span>
<span data-ttu-id="ff49d-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ff49d-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff49d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff49d-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ff49d-105">方法</span><span class="sxs-lookup"><span data-stu-id="ff49d-105">Methods</span></span>  
 <span data-ttu-id="ff49d-106">PeerSecuritySettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="ff49d-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ff49d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="ff49d-107">Properties</span></span>  
 <span data-ttu-id="ff49d-108">PeerSecuritySettings 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="ff49d-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="ff49d-109">模式</span><span class="sxs-lookup"><span data-stu-id="ff49d-109">Mode</span></span>  
 <span data-ttu-id="ff49d-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="ff49d-110">Data type: string</span></span>  
  
 <span data-ttu-id="ff49d-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff49d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff49d-112">使用繫結設定之端點是否採用訊息層級與傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="ff49d-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="ff49d-113">Transport</span><span class="sxs-lookup"><span data-stu-id="ff49d-113">Transport</span></span>  
 <span data-ttu-id="ff49d-114">資料類型：PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ff49d-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="ff49d-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="ff49d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ff49d-116">傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ff49d-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff49d-117">需求</span><span class="sxs-lookup"><span data-stu-id="ff49d-117">Requirements</span></span>  
  
|<span data-ttu-id="ff49d-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ff49d-118">MOF</span></span>|<span data-ttu-id="ff49d-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="ff49d-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ff49d-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="ff49d-120">Namespace</span></span>|<span data-ttu-id="ff49d-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="ff49d-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff49d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff49d-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
