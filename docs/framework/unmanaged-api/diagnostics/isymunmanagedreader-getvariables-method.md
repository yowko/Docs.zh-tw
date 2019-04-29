---
title: ISymUnmanagedReader::GetVariables 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 846ff76fb1073394cc27597c9a2015148581cc70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669997"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="ef5f1-102">ISymUnmanagedReader::GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="ef5f1-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="ef5f1-103">傳回非本機變數，其父系和名稱。</span><span class="sxs-lookup"><span data-stu-id="ef5f1-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef5f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef5f1-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef5f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef5f1-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="ef5f1-106">[in]變數的父代。</span><span class="sxs-lookup"><span data-stu-id="ef5f1-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="ef5f1-107">[in] `pVars` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="ef5f1-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="ef5f1-108">[out]此變數會接收傳入的變數數目的指標`pVars`。</span><span class="sxs-lookup"><span data-stu-id="ef5f1-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="ef5f1-109">[out]接收變數的變數的指標。</span><span class="sxs-lookup"><span data-stu-id="ef5f1-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef5f1-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="ef5f1-110">Return Value</span></span>  
 <span data-ttu-id="ef5f1-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ef5f1-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef5f1-112">需求</span><span class="sxs-lookup"><span data-stu-id="ef5f1-112">Requirements</span></span>  
 <span data-ttu-id="ef5f1-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ef5f1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5f1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef5f1-114">See also</span></span>

- [<span data-ttu-id="ef5f1-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="ef5f1-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
