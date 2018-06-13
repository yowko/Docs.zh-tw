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
ms.openlocfilehash: 0898d554a2602a1139f2e37eb67f3aa00c5bd79e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436081"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="9af81-102">ISymUnmanagedMethod::GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9af81-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="9af81-103">取得圍住儲存指定的位移這個方法內的最封入語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="9af81-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="9af81-104">這可以用來啟動本機變數搜尋。</span><span class="sxs-lookup"><span data-stu-id="9af81-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9af81-105">語法</span><span class="sxs-lookup"><span data-stu-id="9af81-105">Syntax</span></span>  
  
```  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9af81-106">參數</span><span class="sxs-lookup"><span data-stu-id="9af81-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="9af81-107">[in]A`ULONG`包含位移。</span><span class="sxs-lookup"><span data-stu-id="9af81-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9af81-108">[out]設定的指標所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="9af81-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9af81-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9af81-109">Return Value</span></span>  
 <span data-ttu-id="9af81-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="9af81-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af81-111">需求</span><span class="sxs-lookup"><span data-stu-id="9af81-111">Requirements</span></span>  
 <span data-ttu-id="9af81-112">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9af81-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af81-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9af81-113">See Also</span></span>  
 [<span data-ttu-id="9af81-114">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="9af81-114">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
