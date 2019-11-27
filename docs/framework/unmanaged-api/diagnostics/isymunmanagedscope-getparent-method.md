---
title: ISymUnmanagedScope::GetParent 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: 512dd4055a0aad8498db6ef2241c9363aecee9c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446297"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="69513-102">ISymUnmanagedScope::GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="69513-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="69513-103">取得此範圍的父範圍。</span><span class="sxs-lookup"><span data-stu-id="69513-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69513-104">語法</span><span class="sxs-lookup"><span data-stu-id="69513-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69513-105">參數</span><span class="sxs-lookup"><span data-stu-id="69513-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="69513-106">脫銷傳回之[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="69513-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69513-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="69513-107">Return Value</span></span>  
 <span data-ttu-id="69513-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="69513-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69513-109">需求</span><span class="sxs-lookup"><span data-stu-id="69513-109">Requirements</span></span>  
 <span data-ttu-id="69513-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="69513-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69513-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69513-111">See also</span></span>

- [<span data-ttu-id="69513-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="69513-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="69513-113">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="69513-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
