---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="252b1-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="252b1-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="252b1-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="252b1-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="252b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="252b1-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="252b1-105">方法</span><span class="sxs-lookup"><span data-stu-id="252b1-105">Methods</span></span>  
 <span data-ttu-id="252b1-106">SymmetricSecurityBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="252b1-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="252b1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="252b1-107">Properties</span></span>  
 <span data-ttu-id="252b1-108">SymmetricSecurityBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="252b1-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="252b1-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="252b1-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="252b1-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="252b1-110">Data type: string</span></span>  
  
 <span data-ttu-id="252b1-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="252b1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="252b1-112">這個繫結的訊息加密和簽章順序。</span><span class="sxs-lookup"><span data-stu-id="252b1-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="252b1-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="252b1-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="252b1-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="252b1-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="252b1-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="252b1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="252b1-116">繫結是否需要簽章確認。</span><span class="sxs-lookup"><span data-stu-id="252b1-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="252b1-117">需求</span><span class="sxs-lookup"><span data-stu-id="252b1-117">Requirements</span></span>  
  
|<span data-ttu-id="252b1-118">MOF</span><span class="sxs-lookup"><span data-stu-id="252b1-118">MOF</span></span>|<span data-ttu-id="252b1-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="252b1-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="252b1-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="252b1-120">Namespace</span></span>|<span data-ttu-id="252b1-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="252b1-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="252b1-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="252b1-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
