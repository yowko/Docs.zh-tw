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
ms.openlocfilehash: 4590d2734ea89bc1bc8a30db1c7ecac5effafd7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429753"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="8c419-102">ISymUnmanagedReader::GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="8c419-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="8c419-103">傳回非區域變數，並指定其父系和名稱。</span><span class="sxs-lookup"><span data-stu-id="8c419-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c419-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c419-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c419-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c419-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="8c419-106">在變數的父系。</span><span class="sxs-lookup"><span data-stu-id="8c419-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="8c419-107">[in] `pVars` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="8c419-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="8c419-108">脫銷變數的指標，可接收 `pVars`中傳回的變數數目。</span><span class="sxs-lookup"><span data-stu-id="8c419-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="8c419-109">脫銷接收變數之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="8c419-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c419-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8c419-110">Return Value</span></span>  
 <span data-ttu-id="8c419-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8c419-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c419-112">需求</span><span class="sxs-lookup"><span data-stu-id="8c419-112">Requirements</span></span>  
 <span data-ttu-id="8c419-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8c419-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c419-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c419-114">See also</span></span>

- [<span data-ttu-id="8c419-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="8c419-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
