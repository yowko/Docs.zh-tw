---
title: ISymUnmanagedMethod::GetNamespace 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53a47cf67edb36b06c92be83cb23c2e1dd1e75cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424426"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="b9a18-102">ISymUnmanagedMethod::GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="b9a18-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="b9a18-103">取得在其中定義這個方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b9a18-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9a18-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9a18-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9a18-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9a18-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b9a18-106">[out]設定的指標所傳回[ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b9a18-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9a18-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9a18-107">Return Value</span></span>  
 <span data-ttu-id="b9a18-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b9a18-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9a18-109">需求</span><span class="sxs-lookup"><span data-stu-id="b9a18-109">Requirements</span></span>  
 <span data-ttu-id="b9a18-110">**標頭：** 於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b9a18-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a18-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9a18-111">See Also</span></span>  
 [<span data-ttu-id="b9a18-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="b9a18-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
