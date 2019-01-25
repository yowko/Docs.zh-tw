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
ms.openlocfilehash: 61dd9f8a668904bb9b9e0b6b4d1d84d1ed07045d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737880"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="cb784-102">ISymUnmanagedReader::GetGlobalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="cb784-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="cb784-103">傳回所有全域變數。</span><span class="sxs-lookup"><span data-stu-id="cb784-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb784-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb784-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb784-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb784-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="cb784-106">[in]所指向緩衝區的長度`pcVars`。</span><span class="sxs-lookup"><span data-stu-id="cb784-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="cb784-107">[out]指標`ULONG32`接收含有變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="cb784-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="cb784-108">[out]這種緩衝區包含的變數。</span><span class="sxs-lookup"><span data-stu-id="cb784-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb784-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cb784-109">Return Value</span></span>  
 <span data-ttu-id="cb784-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="cb784-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb784-111">需求</span><span class="sxs-lookup"><span data-stu-id="cb784-111">Requirements</span></span>  
 <span data-ttu-id="cb784-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cb784-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb784-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb784-113">See also</span></span>
- [<span data-ttu-id="cb784-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="cb784-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
