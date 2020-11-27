---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 00485ff80a0064e700d99203de3aa581d3761f30
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255724"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="d1dc4-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1dc4-102">AsymmetricSecurityBindingElement</span></span>

<span data-ttu-id="d1dc4-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1dc4-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1dc4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1dc4-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d1dc4-105">方法</span><span class="sxs-lookup"><span data-stu-id="d1dc4-105">Methods</span></span>  

 <span data-ttu-id="d1dc4-106">AsymmetricSecurityBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="d1dc4-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d1dc4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d1dc4-107">Properties</span></span>  

 <span data-ttu-id="d1dc4-108">AsymmetricSecurityBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="d1dc4-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="d1dc4-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="d1dc4-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="d1dc4-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="d1dc4-110">Data type: string</span></span>  
  
 <span data-ttu-id="d1dc4-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d1dc4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1dc4-112">這個繫結的訊息加密和簽章順序。</span><span class="sxs-lookup"><span data-stu-id="d1dc4-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="d1dc4-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="d1dc4-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="d1dc4-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="d1dc4-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d1dc4-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="d1dc4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1dc4-116">繫結是否需要簽章確認。</span><span class="sxs-lookup"><span data-stu-id="d1dc4-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1dc4-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="d1dc4-117">Requirements</span></span>  
  
|<span data-ttu-id="d1dc4-118">MOF</span><span class="sxs-lookup"><span data-stu-id="d1dc4-118">MOF</span></span>|<span data-ttu-id="d1dc4-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="d1dc4-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d1dc4-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="d1dc4-120">Namespace</span></span>|<span data-ttu-id="d1dc4-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="d1dc4-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1dc4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1dc4-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
