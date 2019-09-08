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
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796547"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="9e61e-102">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="9e61e-102">IAssemblyName Interface</span></span>
<span data-ttu-id="9e61e-103">提供方法來描述和使用元件的唯一身分識別。</span><span class="sxs-lookup"><span data-stu-id="9e61e-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e61e-104">方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-104">Methods</span></span>  
  
|<span data-ttu-id="9e61e-105">方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-105">Method</span></span>|<span data-ttu-id="9e61e-106">描述</span><span class="sxs-lookup"><span data-stu-id="9e61e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e61e-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="9e61e-108">建立這個`IAssemblyName`物件的淺層複本。</span><span class="sxs-lookup"><span data-stu-id="9e61e-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9e61e-109">Finalize 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="9e61e-110">允許此`IAssemblyName`物件釋放資源，並執行其他清除作業，再呼叫其析構函式。</span><span class="sxs-lookup"><span data-stu-id="9e61e-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="9e61e-111">GetDisplayName 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="9e61e-112">取得這個`IAssemblyName`物件所參考之元件的人類可讀名稱。</span><span class="sxs-lookup"><span data-stu-id="9e61e-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9e61e-113">GetName 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="9e61e-114">取得這個`IAssemblyName`物件所參考的簡單、未加密的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="9e61e-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9e61e-115">GetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="9e61e-116">取得指定`PropertyId`之所參考之屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="9e61e-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="9e61e-117">GetVersion 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="9e61e-118">取得這個`IAssemblyName`物件所參考之元件的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="9e61e-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="9e61e-119">IsEqual 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="9e61e-120">根據指定的比較`IAssemblyName`旗標，判斷指定`IAssemblyName`的物件是否等於這個。</span><span class="sxs-lookup"><span data-stu-id="9e61e-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="9e61e-121">SetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="9e61e-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="9e61e-122">設定指定`PropertyId`之所參考之屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9e61e-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9e61e-123">需求</span><span class="sxs-lookup"><span data-stu-id="9e61e-123">Requirements</span></span>  
 <span data-ttu-id="9e61e-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e61e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e61e-125">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="9e61e-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9e61e-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e61e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e61e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e61e-127">See also</span></span>

- [<span data-ttu-id="9e61e-128">融合介面</span><span class="sxs-lookup"><span data-stu-id="9e61e-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="9e61e-129">IAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9e61e-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
