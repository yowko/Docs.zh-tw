---
title: 合約
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868437"
---
# <a name="contract"></a><span data-ttu-id="9334a-102">合約</span><span class="sxs-lookup"><span data-stu-id="9334a-102">Contract</span></span>
<span data-ttu-id="9334a-103">合約</span><span class="sxs-lookup"><span data-stu-id="9334a-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9334a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9334a-104">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9334a-105">方法</span><span class="sxs-lookup"><span data-stu-id="9334a-105">Methods</span></span>  
 <span data-ttu-id="9334a-106">Contract 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="9334a-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9334a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9334a-107">Properties</span></span>  
 <span data-ttu-id="9334a-108">Contract 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="9334a-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="9334a-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="9334a-109">AppDomainId</span></span>  
 <span data-ttu-id="9334a-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="9334a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="9334a-111">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-112">裝載合約之的 appdomain 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9334a-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="9334a-113">「行為」</span><span class="sxs-lookup"><span data-stu-id="9334a-113">Behaviors</span></span>  
 <span data-ttu-id="9334a-114">資料類型:行為陣列</span><span class="sxs-lookup"><span data-stu-id="9334a-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="9334a-115">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-116">與此合約有關聯的行為。</span><span class="sxs-lookup"><span data-stu-id="9334a-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="9334a-117">名稱</span><span class="sxs-lookup"><span data-stu-id="9334a-117">Name</span></span>  
 <span data-ttu-id="9334a-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="9334a-118">Data type: string</span></span>  
  
 <span data-ttu-id="9334a-119">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-120">WSDL 中合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="9334a-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="9334a-121">命名空間</span><span class="sxs-lookup"><span data-stu-id="9334a-121">Namespace</span></span>  
 <span data-ttu-id="9334a-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="9334a-122">Data type: string</span></span>  
  
 <span data-ttu-id="9334a-123">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-124">WSDL 中 `portType` 項目的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9334a-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="9334a-125">作業</span><span class="sxs-lookup"><span data-stu-id="9334a-125">Operations</span></span>  
 <span data-ttu-id="9334a-126">資料類型:Operation 陣列</span><span class="sxs-lookup"><span data-stu-id="9334a-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="9334a-127">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-128">此合約的作業。</span><span class="sxs-lookup"><span data-stu-id="9334a-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="9334a-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="9334a-129">ProcessId</span></span>  
 <span data-ttu-id="9334a-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="9334a-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="9334a-131">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-132">裝載合約之處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="9334a-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="9334a-133">ref</span><span class="sxs-lookup"><span data-stu-id="9334a-133">ref</span></span>  
 <span data-ttu-id="9334a-134">資料類型:合約</span><span class="sxs-lookup"><span data-stu-id="9334a-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="9334a-135">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-136">當合約是雙工合約時的回呼類型。</span><span class="sxs-lookup"><span data-stu-id="9334a-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="9334a-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="9334a-137">SessionMode</span></span>  
 <span data-ttu-id="9334a-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="9334a-138">Data type: string</span></span>  
  
 <span data-ttu-id="9334a-139">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-140">代表合約是否需要與此合約關聯的繫結才能使用通道工作階段。</span><span class="sxs-lookup"><span data-stu-id="9334a-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="9334a-141">類型</span><span class="sxs-lookup"><span data-stu-id="9334a-141">Type</span></span>  
 <span data-ttu-id="9334a-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="9334a-142">Data type: string</span></span>  
  
 <span data-ttu-id="9334a-143">存取類型:唯讀</span><span class="sxs-lookup"><span data-stu-id="9334a-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9334a-144">合約的類型。</span><span class="sxs-lookup"><span data-stu-id="9334a-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9334a-145">需求</span><span class="sxs-lookup"><span data-stu-id="9334a-145">Requirements</span></span>  
  
|<span data-ttu-id="9334a-146">MOF</span><span class="sxs-lookup"><span data-stu-id="9334a-146">MOF</span></span>|<span data-ttu-id="9334a-147">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="9334a-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9334a-148">命名空間</span><span class="sxs-lookup"><span data-stu-id="9334a-148">Namespace</span></span>|<span data-ttu-id="9334a-149">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="9334a-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9334a-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9334a-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
