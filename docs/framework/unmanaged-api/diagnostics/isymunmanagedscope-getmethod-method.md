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
ms.openlocfilehash: cdbffe71540b51ff539a45861546efd761761892
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615367"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="6e031-102">ISymUnmanagedScope::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="6e031-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="6e031-103">取得包含此範圍的方法。</span><span class="sxs-lookup"><span data-stu-id="6e031-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e031-104">語法</span><span class="sxs-lookup"><span data-stu-id="6e031-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e031-105">參數</span><span class="sxs-lookup"><span data-stu-id="6e031-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6e031-106">脫銷傳回之[ISymUnmanagedMethod](isymunmanagedmethod-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="6e031-106">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e031-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6e031-107">Return Value</span></span>  
 <span data-ttu-id="6e031-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6e031-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e031-109">需求</span><span class="sxs-lookup"><span data-stu-id="6e031-109">Requirements</span></span>  
 <span data-ttu-id="6e031-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6e031-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e031-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e031-111">See also</span></span>

- [<span data-ttu-id="6e031-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="6e031-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
