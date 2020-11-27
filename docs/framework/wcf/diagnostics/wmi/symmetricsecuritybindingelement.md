---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: c618b5b41790b04a84b4c50fe47baa2c0cb05ab2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274097"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="bc66f-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bc66f-102">SymmetricSecurityBindingElement</span></span>

<span data-ttu-id="bc66f-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bc66f-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc66f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc66f-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bc66f-105">方法</span><span class="sxs-lookup"><span data-stu-id="bc66f-105">Methods</span></span>  

 <span data-ttu-id="bc66f-106">SymmetricSecurityBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="bc66f-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bc66f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bc66f-107">Properties</span></span>  

 <span data-ttu-id="bc66f-108">SymmetricSecurityBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="bc66f-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="bc66f-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="bc66f-109">MessageProtectionOrder</span></span>  

 <span data-ttu-id="bc66f-110">資料類型：字串</span><span class="sxs-lookup"><span data-stu-id="bc66f-110">Data type: string</span></span>  
  
 <span data-ttu-id="bc66f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bc66f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc66f-112">這個繫結的訊息加密和簽章順序。</span><span class="sxs-lookup"><span data-stu-id="bc66f-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="bc66f-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="bc66f-113">RequireSignatureConfirmation</span></span>  

 <span data-ttu-id="bc66f-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="bc66f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="bc66f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="bc66f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bc66f-116">繫結是否需要簽章確認。</span><span class="sxs-lookup"><span data-stu-id="bc66f-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc66f-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="bc66f-117">Requirements</span></span>  
  
|<span data-ttu-id="bc66f-118">MOF</span><span class="sxs-lookup"><span data-stu-id="bc66f-118">MOF</span></span>|<span data-ttu-id="bc66f-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="bc66f-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bc66f-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="bc66f-120">Namespace</span></span>|<span data-ttu-id="bc66f-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="bc66f-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc66f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc66f-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
