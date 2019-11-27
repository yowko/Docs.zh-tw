---
title: ISymUnmanagedMethod::GetScopeFromOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 36b1b2394907f242c0e8c5e277c0d1c5b3b02e1b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448910"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="9ab12-102">ISymUnmanagedMethod::GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9ab12-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="9ab12-103">取得在這個方法中，包含指定之位移的最封入詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="9ab12-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="9ab12-104">這可以用來啟動本機變數搜尋。</span><span class="sxs-lookup"><span data-stu-id="9ab12-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab12-105">語法</span><span class="sxs-lookup"><span data-stu-id="9ab12-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ab12-106">參數</span><span class="sxs-lookup"><span data-stu-id="9ab12-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="9ab12-107">在包含位移的 `ULONG`。</span><span class="sxs-lookup"><span data-stu-id="9ab12-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9ab12-108">脫銷設定為所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="9ab12-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ab12-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9ab12-109">Return Value</span></span>  
 <span data-ttu-id="9ab12-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="9ab12-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ab12-111">需求</span><span class="sxs-lookup"><span data-stu-id="9ab12-111">Requirements</span></span>  
 <span data-ttu-id="9ab12-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="9ab12-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab12-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ab12-113">See also</span></span>

- [<span data-ttu-id="9ab12-114">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="9ab12-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
