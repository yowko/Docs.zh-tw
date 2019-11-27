---
title: ISymUnmanagedMethod::GetToken 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: 048d784a55fd7c29c837a54fbd5adcdcf62a7a2c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448855"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="78608-102">ISymUnmanagedMethod::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="78608-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="78608-103">傳回這個方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="78608-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78608-104">語法</span><span class="sxs-lookup"><span data-stu-id="78608-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78608-105">參數</span><span class="sxs-lookup"><span data-stu-id="78608-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="78608-106">脫銷`mdMethodDef` 的指標，接收包含中繼資料所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="78608-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78608-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="78608-107">Return Value</span></span>  
 <span data-ttu-id="78608-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="78608-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78608-109">需求</span><span class="sxs-lookup"><span data-stu-id="78608-109">Requirements</span></span>  
 <span data-ttu-id="78608-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="78608-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78608-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="78608-111">See also</span></span>

- [<span data-ttu-id="78608-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="78608-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
