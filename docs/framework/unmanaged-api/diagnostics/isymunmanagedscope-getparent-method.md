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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ddf13eb87bd046a2ae7aad39f23112e3ae80c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427955"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="40063-102">ISymUnmanagedScope::GetParent 方法</span><span class="sxs-lookup"><span data-stu-id="40063-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="40063-103">取得此範圍的父範圍。</span><span class="sxs-lookup"><span data-stu-id="40063-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40063-104">語法</span><span class="sxs-lookup"><span data-stu-id="40063-104">Syntax</span></span>  
  
```  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40063-105">參數</span><span class="sxs-lookup"><span data-stu-id="40063-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="40063-106">[out]所傳回的指標[ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="40063-106">[out] A pointer to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40063-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="40063-107">Return Value</span></span>  
 <span data-ttu-id="40063-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="40063-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40063-109">需求</span><span class="sxs-lookup"><span data-stu-id="40063-109">Requirements</span></span>  
 <span data-ttu-id="40063-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="40063-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40063-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40063-111">See Also</span></span>  
 [<span data-ttu-id="40063-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="40063-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="40063-113">GetChildren 方法</span><span class="sxs-lookup"><span data-stu-id="40063-113">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)
