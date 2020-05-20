---
title: ISymUnmanagedScope::GetNamespaces 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
ms.openlocfilehash: 6f11a69671864ba4627c2bb8c86e0c9beb27eeb1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611116"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="0639e-102">ISymUnmanagedScope::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="0639e-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="0639e-103">取得在此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="0639e-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0639e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0639e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0639e-105">參數</span><span class="sxs-lookup"><span data-stu-id="0639e-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="0639e-106">[in] `namespaces` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="0639e-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="0639e-107">脫銷的指標 `ULONG32` ，接收包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="0639e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="0639e-108">脫銷接收命名空間的陣列。</span><span class="sxs-lookup"><span data-stu-id="0639e-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0639e-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="0639e-109">Return Value</span></span>  
 <span data-ttu-id="0639e-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0639e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0639e-111">需求</span><span class="sxs-lookup"><span data-stu-id="0639e-111">Requirements</span></span>  
 <span data-ttu-id="0639e-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="0639e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0639e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0639e-113">See also</span></span>

- [<span data-ttu-id="0639e-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="0639e-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
