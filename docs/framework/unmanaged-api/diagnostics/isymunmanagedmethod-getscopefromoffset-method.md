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
ms.openlocfilehash: cf2784ce0ac6e614e75a341660808b9fe03ada0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699439"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="3bab7-102">ISymUnmanagedMethod::GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="3bab7-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>

<span data-ttu-id="3bab7-103">取得這個方法內的最封閉詞彙範圍，該範圍會括住指定的位移。</span><span class="sxs-lookup"><span data-stu-id="3bab7-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="3bab7-104">這可以用來啟動本機變數搜尋。</span><span class="sxs-lookup"><span data-stu-id="3bab7-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bab7-105">語法</span><span class="sxs-lookup"><span data-stu-id="3bab7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bab7-106">參數</span><span class="sxs-lookup"><span data-stu-id="3bab7-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="3bab7-107">在 `ULONG` 包含位移的。</span><span class="sxs-lookup"><span data-stu-id="3bab7-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3bab7-108">擴展設定為傳回之 [ISymUnmanagedScope](isymunmanagedscope-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="3bab7-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3bab7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3bab7-109">Return Value</span></span>  

 <span data-ttu-id="3bab7-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3bab7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bab7-111">需求</span><span class="sxs-lookup"><span data-stu-id="3bab7-111">Requirements</span></span>  

 <span data-ttu-id="3bab7-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3bab7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bab7-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bab7-113">See also</span></span>

- [<span data-ttu-id="3bab7-114">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="3bab7-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
