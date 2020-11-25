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
ms.openlocfilehash: 59f450117d1a52ce7b900d9d67330fc98281afa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728416"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="89213-102">ICorDebugClass::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="89213-102">ICorDebugClass::GetToken Method</span></span>

<span data-ttu-id="89213-103">取得 `TypeDef` 參考這個類別定義的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="89213-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89213-104">語法</span><span class="sxs-lookup"><span data-stu-id="89213-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89213-105">參數</span><span class="sxs-lookup"><span data-stu-id="89213-105">Parameters</span></span>  

 `pTypeDef`  
 <span data-ttu-id="89213-106">擴展 `mdTypeDef` 參考此類別定義的權杖指標。</span><span class="sxs-lookup"><span data-stu-id="89213-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89213-107">需求</span><span class="sxs-lookup"><span data-stu-id="89213-107">Requirements</span></span>  

 <span data-ttu-id="89213-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89213-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89213-109">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89213-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89213-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89213-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89213-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89213-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89213-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89213-112">See also</span></span>

- [<span data-ttu-id="89213-113">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="89213-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
