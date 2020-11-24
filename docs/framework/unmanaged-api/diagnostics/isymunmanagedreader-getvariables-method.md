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
ms.openlocfilehash: c4341a5ffe557694473ae505590b57d39a27a721
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675889"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="0f79b-102">ISymUnmanagedReader::GetVariables 方法</span><span class="sxs-lookup"><span data-stu-id="0f79b-102">ISymUnmanagedReader::GetVariables Method</span></span>

<span data-ttu-id="0f79b-103">傳回非區域變數，並指定其父系和名稱。</span><span class="sxs-lookup"><span data-stu-id="0f79b-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f79b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0f79b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f79b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0f79b-105">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="0f79b-106">在變數的父系。</span><span class="sxs-lookup"><span data-stu-id="0f79b-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="0f79b-107">[in] `pVars` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="0f79b-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="0f79b-108">擴展變數的指標，此變數會接收中傳回的變數數目 `pVars` 。</span><span class="sxs-lookup"><span data-stu-id="0f79b-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="0f79b-109">擴展接收變數之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="0f79b-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f79b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="0f79b-110">Return Value</span></span>  

 <span data-ttu-id="0f79b-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0f79b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f79b-112">需求</span><span class="sxs-lookup"><span data-stu-id="0f79b-112">Requirements</span></span>  

 <span data-ttu-id="0f79b-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="0f79b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f79b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f79b-114">See also</span></span>

- [<span data-ttu-id="0f79b-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="0f79b-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
