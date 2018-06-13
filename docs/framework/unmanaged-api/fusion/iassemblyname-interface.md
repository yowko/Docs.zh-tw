---
title: IAssemblyName 介面
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa12252c4f2a8e710a4a880af103aa324f8118ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432396"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="1d1de-102">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="1d1de-102">IAssemblyName Interface</span></span>
<span data-ttu-id="1d1de-103">提供方法來描述及使用組件的唯一識別。</span><span class="sxs-lookup"><span data-stu-id="1d1de-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1d1de-104">方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-104">Methods</span></span>  
  
|<span data-ttu-id="1d1de-105">方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-105">Method</span></span>|<span data-ttu-id="1d1de-106">描述</span><span class="sxs-lookup"><span data-stu-id="1d1de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1d1de-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="1d1de-108">建立這樣的淺層複本`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="1d1de-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="1d1de-109">Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="1d1de-110">允許您為此`IAssemblyName`物件釋放資源並呼叫其解構函式之前執行其他清除作業。</span><span class="sxs-lookup"><span data-stu-id="1d1de-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="1d1de-111">GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="1d1de-112">取得人類看得懂的名稱所參考的組件`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="1d1de-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="1d1de-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="1d1de-114">取得所參考的組件的簡單、 未加密名稱`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="1d1de-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="1d1de-115">GetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="1d1de-116">取得所指定參考之屬性的指標`PropertyId`。</span><span class="sxs-lookup"><span data-stu-id="1d1de-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="1d1de-117">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="1d1de-118">取得所參考的組件的版本資訊`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="1d1de-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="1d1de-119">IsEqual 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="1d1de-120">決定指定`IAssemblyName`物件是否等於此`IAssemblyName`，根據指定的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="1d1de-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="1d1de-121">SetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="1d1de-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="1d1de-122">設定所指定參考之屬性的值`PropertyId`。</span><span class="sxs-lookup"><span data-stu-id="1d1de-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1d1de-123">需求</span><span class="sxs-lookup"><span data-stu-id="1d1de-123">Requirements</span></span>  
 <span data-ttu-id="1d1de-124">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d1de-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d1de-125">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1d1de-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1d1de-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d1de-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1de-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d1de-127">See Also</span></span>  
 [<span data-ttu-id="1d1de-128">融合介面</span><span class="sxs-lookup"><span data-stu-id="1d1de-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="1d1de-129">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1d1de-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
