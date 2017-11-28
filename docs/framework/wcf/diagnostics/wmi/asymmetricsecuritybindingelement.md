---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 104810fc24cfe7c4c6ddf7ee5ece9f16a345c80c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="e3cdd-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e3cdd-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="e3cdd-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="e3cdd-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3cdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="e3cdd-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e3cdd-105">方法</span><span class="sxs-lookup"><span data-stu-id="e3cdd-105">Methods</span></span>  
 <span data-ttu-id="e3cdd-106">AsymmetricSecurityBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="e3cdd-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e3cdd-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e3cdd-107">Properties</span></span>  
 <span data-ttu-id="e3cdd-108">AsymmetricSecurityBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e3cdd-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="e3cdd-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="e3cdd-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="e3cdd-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="e3cdd-110">Data type: string</span></span>  
  
 <span data-ttu-id="e3cdd-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e3cdd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e3cdd-112">這個繫結的訊息加密和簽章順序。</span><span class="sxs-lookup"><span data-stu-id="e3cdd-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="e3cdd-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="e3cdd-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="e3cdd-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="e3cdd-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e3cdd-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="e3cdd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e3cdd-116">繫結是否需要簽章確認。</span><span class="sxs-lookup"><span data-stu-id="e3cdd-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3cdd-117">需求</span><span class="sxs-lookup"><span data-stu-id="e3cdd-117">Requirements</span></span>  
  
|<span data-ttu-id="e3cdd-118">MOF</span><span class="sxs-lookup"><span data-stu-id="e3cdd-118">MOF</span></span>|<span data-ttu-id="e3cdd-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="e3cdd-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e3cdd-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="e3cdd-120">Namespace</span></span>|<span data-ttu-id="e3cdd-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="e3cdd-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3cdd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3cdd-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
