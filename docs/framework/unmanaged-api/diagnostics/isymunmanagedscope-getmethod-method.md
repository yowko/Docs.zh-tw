---
title: ISymUnmanagedScope::GetMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 348a8cebe0fd746f3ae490484ffcca2fcb77684b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446323"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="00a40-102">ISymUnmanagedScope::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="00a40-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="00a40-103">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="00a40-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00a40-104">語法</span><span class="sxs-lookup"><span data-stu-id="00a40-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00a40-105">參數</span><span class="sxs-lookup"><span data-stu-id="00a40-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="00a40-106">脫銷傳回之[ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="00a40-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00a40-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="00a40-107">Return Value</span></span>  
 <span data-ttu-id="00a40-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="00a40-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00a40-109">需求</span><span class="sxs-lookup"><span data-stu-id="00a40-109">Requirements</span></span>  
 <span data-ttu-id="00a40-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="00a40-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a40-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00a40-111">See also</span></span>

- [<span data-ttu-id="00a40-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="00a40-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
