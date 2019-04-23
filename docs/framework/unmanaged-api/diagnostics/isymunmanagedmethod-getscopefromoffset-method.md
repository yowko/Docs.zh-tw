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
ms.openlocfilehash: e0e859ba8b6ec247073b0b69b035ea4cf074ab05
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149288"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="bfe29-102">ISymUnmanagedMethod::GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="bfe29-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="bfe29-103">取得包含指定的位移這個方法內的最封入語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="bfe29-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="bfe29-104">這可用來啟動本機變數的搜尋。</span><span class="sxs-lookup"><span data-stu-id="bfe29-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfe29-105">語法</span><span class="sxs-lookup"><span data-stu-id="bfe29-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfe29-106">參數</span><span class="sxs-lookup"><span data-stu-id="bfe29-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="bfe29-107">[in]A`ULONG`包含位移。</span><span class="sxs-lookup"><span data-stu-id="bfe29-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bfe29-108">[out]設定指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="bfe29-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfe29-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="bfe29-109">Return Value</span></span>  
 <span data-ttu-id="bfe29-110">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfe29-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfe29-111">需求</span><span class="sxs-lookup"><span data-stu-id="bfe29-111">Requirements</span></span>  
 <span data-ttu-id="bfe29-112">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bfe29-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe29-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfe29-113">See also</span></span>

- [<span data-ttu-id="bfe29-114">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="bfe29-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
