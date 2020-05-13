---
title: ICorDebugILFrame2::EnumerateTypeParameters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 9020fed83b1c57cae3cc492872a279afb0195983
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205165"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="69231-102">ICorDebugILFrame2::EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="69231-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="69231-103">取得 ICorDebugTypeEnum 物件，其中包含 <xref:System.Type> 此框架中的參數。</span><span class="sxs-lookup"><span data-stu-id="69231-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69231-104">語法</span><span class="sxs-lookup"><span data-stu-id="69231-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69231-105">參數</span><span class="sxs-lookup"><span data-stu-id="69231-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="69231-106">允許列舉型別參數之 ICorDebugTypeEnum 介面物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="69231-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="69231-107">型別參數的清單包含類別型別參數（如果有的話），後面接著方法型別參數（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="69231-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69231-108">備註</span><span class="sxs-lookup"><span data-stu-id="69231-108">Remarks</span></span>  
 <span data-ttu-id="69231-109">請使用[IMetaDataImport2：： EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md)方法來判斷此清單包含多少個類別類型參數和方法類型參數。</span><span class="sxs-lookup"><span data-stu-id="69231-109">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="69231-110">類型參數不一定可供使用。</span><span class="sxs-lookup"><span data-stu-id="69231-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69231-111">需求</span><span class="sxs-lookup"><span data-stu-id="69231-111">Requirements</span></span>  
 <span data-ttu-id="69231-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69231-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69231-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69231-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69231-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69231-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69231-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69231-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
