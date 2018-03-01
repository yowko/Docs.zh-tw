---
title: "ISymUnmanagedReader::GetVariables 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86a0f8ed0a73661b80a9a196682e9539a3b97141
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="a174c-102">ISymUnmanagedReader::GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="a174c-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="a174c-103">傳回非本機變數，其父系和名稱。</span><span class="sxs-lookup"><span data-stu-id="a174c-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a174c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a174c-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a174c-105">參數</span><span class="sxs-lookup"><span data-stu-id="a174c-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="a174c-106">[in]變數的父代。</span><span class="sxs-lookup"><span data-stu-id="a174c-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="a174c-107">[in] `pVars` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="a174c-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="a174c-108">[out]此變數會接收變數中傳回的數目的指標`pVars`。</span><span class="sxs-lookup"><span data-stu-id="a174c-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="a174c-109">[out]接收變數的變數的指標。</span><span class="sxs-lookup"><span data-stu-id="a174c-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a174c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="a174c-110">Return Value</span></span>  
 <span data-ttu-id="a174c-111">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a174c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a174c-112">需求</span><span class="sxs-lookup"><span data-stu-id="a174c-112">Requirements</span></span>  
 <span data-ttu-id="a174c-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a174c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a174c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="a174c-114">See Also</span></span>  
 [<span data-ttu-id="a174c-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="a174c-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
