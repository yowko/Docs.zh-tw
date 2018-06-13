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
ms.openlocfilehash: f67bd427c83385b2433b9f2e97f0b54e3b29a76f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401059"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="635e5-102">ICorDebugClass::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="635e5-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="635e5-103">取得`TypeDef`參考此類別定義的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="635e5-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="635e5-104">語法</span><span class="sxs-lookup"><span data-stu-id="635e5-104">Syntax</span></span>  
  
```  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="635e5-105">參數</span><span class="sxs-lookup"><span data-stu-id="635e5-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="635e5-106">[out]指標`mdTypeDef`參考此類別定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="635e5-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="635e5-107">需求</span><span class="sxs-lookup"><span data-stu-id="635e5-107">Requirements</span></span>  
 <span data-ttu-id="635e5-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="635e5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="635e5-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="635e5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="635e5-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="635e5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="635e5-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="635e5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635e5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="635e5-112">See Also</span></span>  
 [<span data-ttu-id="635e5-113">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="635e5-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
