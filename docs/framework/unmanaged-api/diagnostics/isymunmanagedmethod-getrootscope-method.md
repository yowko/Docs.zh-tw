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
ms.openlocfilehash: 650a64e72b410cddfbee7dce676ddbb5a3b8b3d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614444"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="6f7bc-102">ISymUnmanagedMethod::GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="6f7bc-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="6f7bc-103">取得這個方法內的根詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="6f7bc-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="6f7bc-104">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="6f7bc-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7bc-105">語法</span><span class="sxs-lookup"><span data-stu-id="6f7bc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f7bc-106">參數</span><span class="sxs-lookup"><span data-stu-id="6f7bc-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6f7bc-107">脫銷設定為所傳回[ISymUnmanagedScope](isymunmanagedscope-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="6f7bc-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f7bc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f7bc-108">Return Value</span></span>  
 <span data-ttu-id="6f7bc-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6f7bc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7bc-110">需求</span><span class="sxs-lookup"><span data-stu-id="6f7bc-110">Requirements</span></span>  
 <span data-ttu-id="6f7bc-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6f7bc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7bc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f7bc-112">See also</span></span>

- [<span data-ttu-id="6f7bc-113">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="6f7bc-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
