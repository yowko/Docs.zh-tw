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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d540318dabd55e9a520aedde371e0a83d612721e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759498"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="c887f-102">ISymUnmanagedMethod::GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="c887f-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="c887f-103">取得包含指定的位移這個方法內的最封入語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="c887f-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="c887f-104">這可用來啟動本機變數的搜尋。</span><span class="sxs-lookup"><span data-stu-id="c887f-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c887f-105">語法</span><span class="sxs-lookup"><span data-stu-id="c887f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c887f-106">參數</span><span class="sxs-lookup"><span data-stu-id="c887f-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="c887f-107">[in]A`ULONG`包含位移。</span><span class="sxs-lookup"><span data-stu-id="c887f-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c887f-108">[out]設定指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="c887f-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c887f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c887f-109">Return Value</span></span>  
 <span data-ttu-id="c887f-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="c887f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c887f-111">需求</span><span class="sxs-lookup"><span data-stu-id="c887f-111">Requirements</span></span>  
 <span data-ttu-id="c887f-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c887f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c887f-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c887f-113">See also</span></span>

- [<span data-ttu-id="c887f-114">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="c887f-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
