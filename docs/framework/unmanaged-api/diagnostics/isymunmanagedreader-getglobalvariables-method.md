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
ms.openlocfilehash: 20bfb3e48f411524bd4d9798f17dd935595a12bb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615016"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="8a5b5-102">ISymUnmanagedReader::GetGlobalVariables 方法</span><span class="sxs-lookup"><span data-stu-id="8a5b5-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="8a5b5-103">傳回所有全域變數。</span><span class="sxs-lookup"><span data-stu-id="8a5b5-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a5b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="8a5b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a5b5-105">參數</span><span class="sxs-lookup"><span data-stu-id="8a5b5-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="8a5b5-106">在所指向之緩衝區的長度 `pcVars` 。</span><span class="sxs-lookup"><span data-stu-id="8a5b5-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="8a5b5-107">脫銷的指標 `ULONG32` ，接收包含變數所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="8a5b5-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="8a5b5-108">脫銷包含變數的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="8a5b5-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a5b5-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a5b5-109">Return Value</span></span>  
 <span data-ttu-id="8a5b5-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8a5b5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a5b5-111">需求</span><span class="sxs-lookup"><span data-stu-id="8a5b5-111">Requirements</span></span>  
 <span data-ttu-id="8a5b5-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8a5b5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a5b5-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a5b5-113">See also</span></span>

- [<span data-ttu-id="8a5b5-114">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="8a5b5-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
