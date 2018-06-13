---
title: ISymUnmanagedVariable::GetStartOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b25d072ab96b822e79c6f87f535096550e4bb53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427059"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="fb93c-102">ISymUnmanagedVariable::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="fb93c-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="fb93c-103">取得其父系內這個變數的起始位移。</span><span class="sxs-lookup"><span data-stu-id="fb93c-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="fb93c-104">如果這是在範圍內的區域變數的起始位移會落在範圍定義的位移。</span><span class="sxs-lookup"><span data-stu-id="fb93c-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb93c-105">語法</span><span class="sxs-lookup"><span data-stu-id="fb93c-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb93c-106">參數</span><span class="sxs-lookup"><span data-stu-id="fb93c-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fb93c-107">[out]指標`ULONG32`接收的起始位移。</span><span class="sxs-lookup"><span data-stu-id="fb93c-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb93c-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="fb93c-108">Return Value</span></span>  
 <span data-ttu-id="fb93c-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="fb93c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb93c-110">需求</span><span class="sxs-lookup"><span data-stu-id="fb93c-110">Requirements</span></span>  
 <span data-ttu-id="fb93c-111">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fb93c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb93c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb93c-112">See Also</span></span>  
 [<span data-ttu-id="fb93c-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="fb93c-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="fb93c-114">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="fb93c-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
