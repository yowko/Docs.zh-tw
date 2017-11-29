---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e92c5d804fca3c04506e951a5c341c89eed1c54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="contract"></a><span data-ttu-id="8eed9-102">合約</span><span class="sxs-lookup"><span data-stu-id="8eed9-102">Contract</span></span>
<span data-ttu-id="8eed9-103">合約</span><span class="sxs-lookup"><span data-stu-id="8eed9-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eed9-104">語法</span><span class="sxs-lookup"><span data-stu-id="8eed9-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="8eed9-105">方法</span><span class="sxs-lookup"><span data-stu-id="8eed9-105">Methods</span></span>  
 <span data-ttu-id="8eed9-106">Contract 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="8eed9-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8eed9-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8eed9-107">Properties</span></span>  
 <span data-ttu-id="8eed9-108">Contract 類別有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="8eed9-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="8eed9-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="8eed9-109">AppDomainId</span></span>  
 <span data-ttu-id="8eed9-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="8eed9-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="8eed9-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-112">裝載合約之的 appdomain 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8eed9-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="8eed9-113">行為</span><span class="sxs-lookup"><span data-stu-id="8eed9-113">Behaviors</span></span>  
 <span data-ttu-id="8eed9-114">資料型別：行為陣列</span><span class="sxs-lookup"><span data-stu-id="8eed9-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="8eed9-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-116">與此合約有關聯的行為。</span><span class="sxs-lookup"><span data-stu-id="8eed9-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="8eed9-117">名稱</span><span class="sxs-lookup"><span data-stu-id="8eed9-117">Name</span></span>  
 <span data-ttu-id="8eed9-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="8eed9-118">Data type: string</span></span>  
  
 <span data-ttu-id="8eed9-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-120">WSDL 中合約的名稱。</span><span class="sxs-lookup"><span data-stu-id="8eed9-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="8eed9-121">命名空間</span><span class="sxs-lookup"><span data-stu-id="8eed9-121">Namespace</span></span>  
 <span data-ttu-id="8eed9-122">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="8eed9-122">Data type: string</span></span>  
  
 <span data-ttu-id="8eed9-123">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-124">WSDL 中 `portType` 項目的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8eed9-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="8eed9-125">作業</span><span class="sxs-lookup"><span data-stu-id="8eed9-125">Operations</span></span>  
 <span data-ttu-id="8eed9-126">資料型別：作業陣列</span><span class="sxs-lookup"><span data-stu-id="8eed9-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="8eed9-127">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-128">此合約的作業。</span><span class="sxs-lookup"><span data-stu-id="8eed9-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="8eed9-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="8eed9-129">ProcessId</span></span>  
 <span data-ttu-id="8eed9-130">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="8eed9-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="8eed9-131">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-132">裝載合約之處理序的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="8eed9-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="8eed9-133">ref</span><span class="sxs-lookup"><span data-stu-id="8eed9-133">ref</span></span>  
 <span data-ttu-id="8eed9-134">資料型別：合約</span><span class="sxs-lookup"><span data-stu-id="8eed9-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="8eed9-135">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-136">當合約是雙工合約時的回呼類型。</span><span class="sxs-lookup"><span data-stu-id="8eed9-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="8eed9-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="8eed9-137">SessionMode</span></span>  
 <span data-ttu-id="8eed9-138">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="8eed9-138">Data type: string</span></span>  
  
 <span data-ttu-id="8eed9-139">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-140">代表合約是否需要與此合約關聯的繫結才能使用通道工作階段。</span><span class="sxs-lookup"><span data-stu-id="8eed9-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="8eed9-141">類型</span><span class="sxs-lookup"><span data-stu-id="8eed9-141">Type</span></span>  
 <span data-ttu-id="8eed9-142">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="8eed9-142">Data type: string</span></span>  
  
 <span data-ttu-id="8eed9-143">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="8eed9-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8eed9-144">合約的類型。</span><span class="sxs-lookup"><span data-stu-id="8eed9-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eed9-145">需求</span><span class="sxs-lookup"><span data-stu-id="8eed9-145">Requirements</span></span>  
  
|<span data-ttu-id="8eed9-146">MOF</span><span class="sxs-lookup"><span data-stu-id="8eed9-146">MOF</span></span>|<span data-ttu-id="8eed9-147">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="8eed9-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8eed9-148">命名空間</span><span class="sxs-lookup"><span data-stu-id="8eed9-148">Namespace</span></span>|<span data-ttu-id="8eed9-149">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="8eed9-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8eed9-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8eed9-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
