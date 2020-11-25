---
title: ISymUnmanagedMethod::GetRootScope 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
ms.openlocfilehash: 071738c8fb9b40457215e21172240aa7e77198cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699465"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="1f6f6-102">ISymUnmanagedMethod::GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="1f6f6-102">ISymUnmanagedMethod::GetRootScope Method</span></span>

<span data-ttu-id="1f6f6-103">取得此方法內的根詞彙範圍。</span><span class="sxs-lookup"><span data-stu-id="1f6f6-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="1f6f6-104">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="1f6f6-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6f6-105">語法</span><span class="sxs-lookup"><span data-stu-id="1f6f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f6f6-106">參數</span><span class="sxs-lookup"><span data-stu-id="1f6f6-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1f6f6-107">擴展設定為傳回之 [ISymUnmanagedScope](isymunmanagedscope-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="1f6f6-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f6f6-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="1f6f6-108">Return Value</span></span>  

 <span data-ttu-id="1f6f6-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="1f6f6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f6f6-110">需求</span><span class="sxs-lookup"><span data-stu-id="1f6f6-110">Requirements</span></span>  

 <span data-ttu-id="1f6f6-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="1f6f6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6f6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f6f6-112">See also</span></span>

- [<span data-ttu-id="1f6f6-113">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="1f6f6-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
