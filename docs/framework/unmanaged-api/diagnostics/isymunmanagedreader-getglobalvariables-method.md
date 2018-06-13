---
title: ISymUnmanagedReader::GetGlobalVariables 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6574c4d30b963ce571343d1a584bfccb48ffd195
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430447"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="c9f79-102">ISymUnmanagedReader::GetGlobalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="c9f79-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="c9f79-103">傳回所有的全域變數。</span><span class="sxs-lookup"><span data-stu-id="c9f79-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f79-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9f79-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9f79-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9f79-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="c9f79-106">[in]所指向之緩衝區的長度`pcVars`。</span><span class="sxs-lookup"><span data-stu-id="c9f79-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="c9f79-107">[out]指標`ULONG32`包含變數所需要的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c9f79-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="c9f79-108">[out]這種緩衝區包含的變數。</span><span class="sxs-lookup"><span data-stu-id="c9f79-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9f79-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c9f79-109">Return Value</span></span>  
 <span data-ttu-id="c9f79-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9f79-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f79-111">需求</span><span class="sxs-lookup"><span data-stu-id="c9f79-111">Requirements</span></span>  
 <span data-ttu-id="c9f79-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9f79-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f79-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9f79-113">See Also</span></span>  
 [<span data-ttu-id="c9f79-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="c9f79-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
