---
title: ICorDebugType::GetRank 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f112e0d064041a877963939b78029da08bbbed1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417650"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="f5f69-102">ICorDebugType::GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="f5f69-102">ICorDebugType::GetRank Method</span></span>
<span data-ttu-id="f5f69-103">取得陣列型別中的維度數目。</span><span class="sxs-lookup"><span data-stu-id="f5f69-103">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5f69-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5f69-104">Syntax</span></span>  
  
```  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5f69-105">參數</span><span class="sxs-lookup"><span data-stu-id="f5f69-105">Parameters</span></span>  
 `pnRank`  
 <span data-ttu-id="f5f69-106">[out]維度的數目指標。</span><span class="sxs-lookup"><span data-stu-id="f5f69-106">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5f69-107">需求</span><span class="sxs-lookup"><span data-stu-id="f5f69-107">Requirements</span></span>  
 <span data-ttu-id="f5f69-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5f69-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5f69-109">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5f69-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5f69-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5f69-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5f69-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5f69-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
