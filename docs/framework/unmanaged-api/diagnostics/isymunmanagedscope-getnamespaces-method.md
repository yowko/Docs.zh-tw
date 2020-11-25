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
ms.openlocfilehash: 026ba35044bc7573dc54617dcade9cf3918a76ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725920"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="36331-102">ISymUnmanagedScope::GetNamespaces 方法</span><span class="sxs-lookup"><span data-stu-id="36331-102">ISymUnmanagedScope::GetNamespaces Method</span></span>

<span data-ttu-id="36331-103">取得在此範圍內使用的命名空間。</span><span class="sxs-lookup"><span data-stu-id="36331-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36331-104">語法</span><span class="sxs-lookup"><span data-stu-id="36331-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36331-105">參數</span><span class="sxs-lookup"><span data-stu-id="36331-105">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="36331-106">[in] `namespaces` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="36331-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="36331-107">擴展的指標 `ULONG32` ，會接收包含命名空間所需的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="36331-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="36331-108">擴展接收命名空間的陣列。</span><span class="sxs-lookup"><span data-stu-id="36331-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36331-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="36331-109">Return Value</span></span>  

 <span data-ttu-id="36331-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="36331-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36331-111">需求</span><span class="sxs-lookup"><span data-stu-id="36331-111">Requirements</span></span>  

 <span data-ttu-id="36331-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="36331-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36331-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36331-113">See also</span></span>

- [<span data-ttu-id="36331-114">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="36331-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
