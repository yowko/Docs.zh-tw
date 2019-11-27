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
ms.openlocfilehash: c956f5d68c992f1b08988e59038e8667b391f734
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448923"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="8fd9a-102">ISymUnmanagedMethod::GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="8fd9a-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="8fd9a-103">取得這個方法內的根詞法範圍。</span><span class="sxs-lookup"><span data-stu-id="8fd9a-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="8fd9a-104">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="8fd9a-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fd9a-105">語法</span><span class="sxs-lookup"><span data-stu-id="8fd9a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fd9a-106">參數</span><span class="sxs-lookup"><span data-stu-id="8fd9a-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8fd9a-107">脫銷設定為所傳回[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="8fd9a-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fd9a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8fd9a-108">Return Value</span></span>  
 <span data-ttu-id="8fd9a-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8fd9a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fd9a-110">需求</span><span class="sxs-lookup"><span data-stu-id="8fd9a-110">Requirements</span></span>  
 <span data-ttu-id="8fd9a-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8fd9a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fd9a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fd9a-112">See also</span></span>

- [<span data-ttu-id="8fd9a-113">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="8fd9a-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
