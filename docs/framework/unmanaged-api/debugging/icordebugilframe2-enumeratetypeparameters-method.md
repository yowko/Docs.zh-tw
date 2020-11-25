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
ms.openlocfilehash: 73c17864047270302dbc115667eec4bf5ea1569d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725036"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="62b3e-102">ICorDebugILFrame2::EnumerateTypeParameters 方法</span><span class="sxs-lookup"><span data-stu-id="62b3e-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="62b3e-103">取得 ICorDebugTypeEnum 物件，其中包含 <xref:System.Type> 此框架中的參數。</span><span class="sxs-lookup"><span data-stu-id="62b3e-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62b3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="62b3e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62b3e-105">參數</span><span class="sxs-lookup"><span data-stu-id="62b3e-105">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="62b3e-106">ICorDebugTypeEnum 介面物件位址的指標，該物件允許型別參數的列舉。</span><span class="sxs-lookup"><span data-stu-id="62b3e-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="62b3e-107">型別參數的清單包含類別型別參數 (如果有任何) 後面接著方法型別參數， () 。</span><span class="sxs-lookup"><span data-stu-id="62b3e-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62b3e-108">備註</span><span class="sxs-lookup"><span data-stu-id="62b3e-108">Remarks</span></span>  

 <span data-ttu-id="62b3e-109">您可以使用 [IMetaDataImport2：： EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) 方法來判斷此清單所包含的類別型別參數和方法類型參數數目。</span><span class="sxs-lookup"><span data-stu-id="62b3e-109">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="62b3e-110">類型參數不一定可以使用。</span><span class="sxs-lookup"><span data-stu-id="62b3e-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62b3e-111">需求</span><span class="sxs-lookup"><span data-stu-id="62b3e-111">Requirements</span></span>  

 <span data-ttu-id="62b3e-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62b3e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62b3e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62b3e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62b3e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62b3e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62b3e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62b3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
