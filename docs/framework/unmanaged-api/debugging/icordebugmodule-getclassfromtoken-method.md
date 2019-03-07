---
title: ICorDebugModule::GetClassFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetClassFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetClassFromToken
helpviewer_keywords:
- GetClassFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetClassFromToken method [.NET Framework debugging]
ms.assetid: 622a4d3c-0425-4c54-a7e4-0735377cdad2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 413e56a65f4966467f487787172973834ac4a65a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496868"
---
# <a name="icordebugmodulegetclassfromtoken-method"></a><span data-ttu-id="a70f0-102">ICorDebugModule::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="a70f0-102">ICorDebugModule::GetClassFromToken Method</span></span>
<span data-ttu-id="a70f0-103">取得指定中繼資料語彙基元的類別。</span><span class="sxs-lookup"><span data-stu-id="a70f0-103">Gets the class specified by the metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a70f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a70f0-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  mdTypeDef        typeDef,  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a70f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="a70f0-105">Parameters</span></span>  
 `typedef`  
 <span data-ttu-id="a70f0-106">[in]`mdTypeDef`參考類別的中繼資料的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a70f0-106">[in] An `mdTypeDef` metadata token that references the metadata of a class.</span></span>  
  
 `ppClass`  
 <span data-ttu-id="a70f0-107">[out]ICorDebugClass 物件，表示類別的位址指標。</span><span class="sxs-lookup"><span data-stu-id="a70f0-107">[out] A pointer to the address of an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a70f0-108">需求</span><span class="sxs-lookup"><span data-stu-id="a70f0-108">Requirements</span></span>  
 <span data-ttu-id="a70f0-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a70f0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a70f0-110">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a70f0-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a70f0-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a70f0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a70f0-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a70f0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
