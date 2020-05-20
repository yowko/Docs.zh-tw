---
title: ISymUnmanagedScope::GetLocalCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 9ffba23e3821c48c9b0708e4b6b617db4ddc5959
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611259"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="2d13f-102">ISymUnmanagedScope::GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="2d13f-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="2d13f-103">取得在此範圍內定義的區域變數計數。</span><span class="sxs-lookup"><span data-stu-id="2d13f-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d13f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2d13f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d13f-105">參數</span><span class="sxs-lookup"><span data-stu-id="2d13f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2d13f-106">脫銷`ULONG32`接收本機變數計數的指標。</span><span class="sxs-lookup"><span data-stu-id="2d13f-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d13f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d13f-107">Return Value</span></span>  
 <span data-ttu-id="2d13f-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2d13f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d13f-109">需求</span><span class="sxs-lookup"><span data-stu-id="2d13f-109">Requirements</span></span>  
 <span data-ttu-id="2d13f-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="2d13f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d13f-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d13f-111">See also</span></span>

- [<span data-ttu-id="2d13f-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="2d13f-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
