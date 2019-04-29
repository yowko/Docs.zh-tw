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
ms.openlocfilehash: 0d8d59ef282818dd9852d0ff8d2ec2abd40986d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697923"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="36426-102">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="36426-102">IAssemblyName Interface</span></span>
<span data-ttu-id="36426-103">提供方法來描述和使用組件的唯一身分識別。</span><span class="sxs-lookup"><span data-stu-id="36426-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36426-104">方法</span><span class="sxs-lookup"><span data-stu-id="36426-104">Methods</span></span>  
  
|<span data-ttu-id="36426-105">方法</span><span class="sxs-lookup"><span data-stu-id="36426-105">Method</span></span>|<span data-ttu-id="36426-106">描述</span><span class="sxs-lookup"><span data-stu-id="36426-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36426-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="36426-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="36426-108">建立這個的淺層複製`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="36426-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="36426-109">Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="36426-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="36426-110">這可讓`IAssemblyName`物件釋放資源並呼叫其解構函式之前執行其他清除作業。</span><span class="sxs-lookup"><span data-stu-id="36426-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="36426-111">GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="36426-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="36426-112">取得人類可讀名稱所參考的組件`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="36426-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="36426-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="36426-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="36426-114">取得所參考的組件的簡單且未加密名稱`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="36426-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="36426-115">GetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="36426-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="36426-116">取得所指定參考之屬性的指標`PropertyId`。</span><span class="sxs-lookup"><span data-stu-id="36426-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="36426-117">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="36426-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="36426-118">取得所參考的組件的版本資訊`IAssemblyName`物件。</span><span class="sxs-lookup"><span data-stu-id="36426-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="36426-119">IsEqual 方法</span><span class="sxs-lookup"><span data-stu-id="36426-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="36426-120">判斷指定`IAssemblyName`物件是否等於這個`IAssemblyName`，根據指定的比較旗標。</span><span class="sxs-lookup"><span data-stu-id="36426-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="36426-121">SetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="36426-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="36426-122">設定所指定參考之屬性的值`PropertyId`。</span><span class="sxs-lookup"><span data-stu-id="36426-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36426-123">需求</span><span class="sxs-lookup"><span data-stu-id="36426-123">Requirements</span></span>  
 <span data-ttu-id="36426-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36426-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36426-125">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="36426-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="36426-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36426-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36426-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36426-127">See also</span></span>

- [<span data-ttu-id="36426-128">融合介面</span><span class="sxs-lookup"><span data-stu-id="36426-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="36426-129">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="36426-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
