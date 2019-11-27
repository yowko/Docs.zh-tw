---
title: ISymUnmanagedScope2::GetConstantCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: f795147bdcd822db90106c7f2171eb1771b1126f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446250"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="c798f-102">ISymUnmanagedScope2::GetConstantCount 方法</span><span class="sxs-lookup"><span data-stu-id="c798f-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="c798f-103">取得在此範圍內定義的常數計數。</span><span class="sxs-lookup"><span data-stu-id="c798f-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c798f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c798f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c798f-105">參數</span><span class="sxs-lookup"><span data-stu-id="c798f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c798f-106">脫銷`ULONG32` 的指標，接收包含常數所需的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="c798f-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c798f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c798f-107">Return Value</span></span>  
 <span data-ttu-id="c798f-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c798f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c798f-109">需求</span><span class="sxs-lookup"><span data-stu-id="c798f-109">Requirements</span></span>  
 <span data-ttu-id="c798f-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c798f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c798f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c798f-111">See also</span></span>

- [<span data-ttu-id="c798f-112">ISymUnmanagedScope2 介面</span><span class="sxs-lookup"><span data-stu-id="c798f-112">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
