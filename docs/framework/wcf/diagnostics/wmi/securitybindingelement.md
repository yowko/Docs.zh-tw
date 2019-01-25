---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: f7c4e30b72af36de1d3088e4ca8cd98ced734104
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692320"
---
# <a name="securitybindingelement"></a><span data-ttu-id="a6697-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a6697-102">SecurityBindingElement</span></span>
<span data-ttu-id="a6697-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a6697-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6697-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6697-104">Syntax</span></span>  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a6697-105">方法</span><span class="sxs-lookup"><span data-stu-id="a6697-105">Methods</span></span>  
 <span data-ttu-id="a6697-106">SecurityBindingElement 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="a6697-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a6697-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a6697-107">Properties</span></span>  
 <span data-ttu-id="a6697-108">SecurityBindingElement 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="a6697-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="a6697-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="a6697-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="a6697-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a6697-110">Data type: string</span></span>  
  
 <span data-ttu-id="a6697-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a6697-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6697-112">指定要與繫結一起使用的演算法。</span><span class="sxs-lookup"><span data-stu-id="a6697-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="a6697-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="a6697-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="a6697-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="a6697-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="a6697-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a6697-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6697-116">布林值，這個值會指定每個訊息是否包含時間戳記。</span><span class="sxs-lookup"><span data-stu-id="a6697-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="a6697-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="a6697-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="a6697-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a6697-118">Data type: string</span></span>  
  
 <span data-ttu-id="a6697-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a6697-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6697-120">用於建立金鑰的 Entropy 來源。</span><span class="sxs-lookup"><span data-stu-id="a6697-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="a6697-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="a6697-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="a6697-122">資料類型：LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="a6697-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="a6697-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a6697-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6697-124">用於本機服務的繫結特定安全性屬性。</span><span class="sxs-lookup"><span data-stu-id="a6697-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="a6697-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="a6697-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="a6697-126">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a6697-126">Data type: string</span></span>  
  
 <span data-ttu-id="a6697-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a6697-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6697-128">用於訊息安全性的版本。</span><span class="sxs-lookup"><span data-stu-id="a6697-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="a6697-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="a6697-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="a6697-130">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="a6697-130">Data type: string</span></span>  
  
 <span data-ttu-id="a6697-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="a6697-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a6697-132">此繫結之安全性標頭中的項目順序。</span><span class="sxs-lookup"><span data-stu-id="a6697-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6697-133">需求</span><span class="sxs-lookup"><span data-stu-id="a6697-133">Requirements</span></span>  
  
|<span data-ttu-id="a6697-134">MOF</span><span class="sxs-lookup"><span data-stu-id="a6697-134">MOF</span></span>|<span data-ttu-id="a6697-135">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="a6697-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a6697-136">命名空間</span><span class="sxs-lookup"><span data-stu-id="a6697-136">Namespace</span></span>|<span data-ttu-id="a6697-137">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="a6697-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6697-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6697-138">See also</span></span>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
