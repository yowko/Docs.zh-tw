---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770408"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="965b6-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="965b6-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="965b6-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="965b6-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="965b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="965b6-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="965b6-105">方法</span><span class="sxs-lookup"><span data-stu-id="965b6-105">Methods</span></span>  
 <span data-ttu-id="965b6-106">SymmetricSecurityBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="965b6-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="965b6-107">屬性</span><span class="sxs-lookup"><span data-stu-id="965b6-107">Properties</span></span>  
 <span data-ttu-id="965b6-108">SymmetricSecurityBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="965b6-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="965b6-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="965b6-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="965b6-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="965b6-110">Data type: string</span></span>  
  
 <span data-ttu-id="965b6-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="965b6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="965b6-112">這個繫結的訊息加密和簽章順序。</span><span class="sxs-lookup"><span data-stu-id="965b6-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="965b6-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="965b6-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="965b6-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="965b6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="965b6-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="965b6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="965b6-116">繫結是否需要簽章確認。</span><span class="sxs-lookup"><span data-stu-id="965b6-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="965b6-117">需求</span><span class="sxs-lookup"><span data-stu-id="965b6-117">Requirements</span></span>  
  
|<span data-ttu-id="965b6-118">MOF</span><span class="sxs-lookup"><span data-stu-id="965b6-118">MOF</span></span>|<span data-ttu-id="965b6-119">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="965b6-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="965b6-120">命名空間</span><span class="sxs-lookup"><span data-stu-id="965b6-120">Namespace</span></span>|<span data-ttu-id="965b6-121">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="965b6-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="965b6-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="965b6-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
