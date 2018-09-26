---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
ms.openlocfilehash: 180b64f6f37e5c765585e52b292319816618be28
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198848"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="a8c1e-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a8c1e-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="a8c1e-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a8c1e-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c1e-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8c1e-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a8c1e-105">方法</span><span class="sxs-lookup"><span data-stu-id="a8c1e-105">Methods</span></span>  
 <span data-ttu-id="a8c1e-106">SymmetricSecurityBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a8c1e-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a8c1e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a8c1e-107">Properties</span></span>  
 <span data-ttu-id="a8c1e-108">SymmetricSecurityBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a8c1e-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="a8c1e-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="a8c1e-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="a8c1e-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a8c1e-110">Data type: string</span></span>  
  
 <span data-ttu-id="a8c1e-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a8c1e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8c1e-112">這個繫結的訊息加密和簽章順序。</span><span class="sxs-lookup"><span data-stu-id="a8c1e-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="a8c1e-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="a8c1e-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="a8c1e-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="a8c1e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a8c1e-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a8c1e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a8c1e-116">繫結是否需要簽章確認。</span><span class="sxs-lookup"><span data-stu-id="a8c1e-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8c1e-117">需求</span><span class="sxs-lookup"><span data-stu-id="a8c1e-117">Requirements</span></span>  
  
|<span data-ttu-id="a8c1e-118">MOF</span><span class="sxs-lookup"><span data-stu-id="a8c1e-118">MOF</span></span>|<span data-ttu-id="a8c1e-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a8c1e-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a8c1e-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="a8c1e-120">Namespace</span></span>|<span data-ttu-id="a8c1e-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a8c1e-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8c1e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8c1e-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
