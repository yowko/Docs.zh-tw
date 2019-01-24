---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 761ed0e30c6acca8c910c5dc97dfbae46c1f89bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564834"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="f1b4c-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f1b4c-102">PeerSecuritySettings</span></span>
<span data-ttu-id="f1b4c-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f1b4c-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1b4c-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f1b4c-105">方法</span><span class="sxs-lookup"><span data-stu-id="f1b4c-105">Methods</span></span>  
 <span data-ttu-id="f1b4c-106">PeerSecuritySettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f1b4c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f1b4c-107">Properties</span></span>  
 <span data-ttu-id="f1b4c-108">PeerSecuritySettings 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="f1b4c-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="f1b4c-109">模式</span><span class="sxs-lookup"><span data-stu-id="f1b4c-109">Mode</span></span>  
 <span data-ttu-id="f1b4c-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="f1b4c-110">Data type: string</span></span>  
  
 <span data-ttu-id="f1b4c-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f1b4c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f1b4c-112">使用繫結設定之端點是否採用訊息層級與傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="f1b4c-113">Transport</span><span class="sxs-lookup"><span data-stu-id="f1b4c-113">Transport</span></span>  
 <span data-ttu-id="f1b4c-114">資料類型：PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f1b4c-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="f1b4c-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="f1b4c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f1b4c-116">傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1b4c-117">需求</span><span class="sxs-lookup"><span data-stu-id="f1b4c-117">Requirements</span></span>  
  
|<span data-ttu-id="f1b4c-118">MOF</span><span class="sxs-lookup"><span data-stu-id="f1b4c-118">MOF</span></span>|<span data-ttu-id="f1b4c-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="f1b4c-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f1b4c-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="f1b4c-120">Namespace</span></span>|<span data-ttu-id="f1b4c-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="f1b4c-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1b4c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1b4c-122">See also</span></span>
- <xref:System.ServiceModel.PeerSecuritySettings>
