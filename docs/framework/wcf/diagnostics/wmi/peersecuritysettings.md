---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="834e6-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="834e6-102">PeerSecuritySettings</span></span>
<span data-ttu-id="834e6-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="834e6-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="834e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="834e6-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="834e6-105">方法</span><span class="sxs-lookup"><span data-stu-id="834e6-105">Methods</span></span>  
 <span data-ttu-id="834e6-106">PeerSecuritySettings 類別並未定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="834e6-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="834e6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="834e6-107">Properties</span></span>  
 <span data-ttu-id="834e6-108">PeerSecuritySettings 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="834e6-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="834e6-109">模式</span><span class="sxs-lookup"><span data-stu-id="834e6-109">Mode</span></span>  
 <span data-ttu-id="834e6-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="834e6-110">Data type: string</span></span>  
  
 <span data-ttu-id="834e6-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="834e6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="834e6-112">使用繫結設定之端點是否採用訊息層級與傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="834e6-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="834e6-113">Transport</span><span class="sxs-lookup"><span data-stu-id="834e6-113">Transport</span></span>  
 <span data-ttu-id="834e6-114">資料型別：PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="834e6-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="834e6-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="834e6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="834e6-116">傳輸安全性設定。</span><span class="sxs-lookup"><span data-stu-id="834e6-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="834e6-117">需求</span><span class="sxs-lookup"><span data-stu-id="834e6-117">Requirements</span></span>  
  
|<span data-ttu-id="834e6-118">MOF</span><span class="sxs-lookup"><span data-stu-id="834e6-118">MOF</span></span>|<span data-ttu-id="834e6-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="834e6-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="834e6-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="834e6-120">Namespace</span></span>|<span data-ttu-id="834e6-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="834e6-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="834e6-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="834e6-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
