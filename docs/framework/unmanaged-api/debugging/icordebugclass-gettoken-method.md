---
title: ICorDebugClass::GetToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4f33bb15a351be5fe8318dcc3339d429dec039e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183699"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="86bb2-102">ICorDebugClass::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="86bb2-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="86bb2-103">取得`TypeDef`參考此類別定義的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="86bb2-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86bb2-104">語法</span><span class="sxs-lookup"><span data-stu-id="86bb2-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86bb2-105">參數</span><span class="sxs-lookup"><span data-stu-id="86bb2-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="86bb2-106">[out]指標`mdTypeDef`參考此類別定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="86bb2-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86bb2-107">需求</span><span class="sxs-lookup"><span data-stu-id="86bb2-107">Requirements</span></span>  
 <span data-ttu-id="86bb2-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86bb2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86bb2-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86bb2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86bb2-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86bb2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86bb2-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86bb2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86bb2-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86bb2-112">See also</span></span>

- [<span data-ttu-id="86bb2-113">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="86bb2-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
