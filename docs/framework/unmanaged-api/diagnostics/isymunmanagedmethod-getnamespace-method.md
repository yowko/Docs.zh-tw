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
ms.openlocfilehash: cda30f3c73bf75c37ff79fc415e02382b053807e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614483"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="6dfea-102">ISymUnmanagedMethod::GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="6dfea-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="6dfea-103">取得在其中定義這個方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6dfea-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfea-104">語法</span><span class="sxs-lookup"><span data-stu-id="6dfea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dfea-105">參數</span><span class="sxs-lookup"><span data-stu-id="6dfea-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6dfea-106">脫銷設定為所傳回[ISymUnmanagedNamespace](isymunmanagednamespace-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="6dfea-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dfea-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="6dfea-107">Return Value</span></span>  
 <span data-ttu-id="6dfea-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6dfea-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dfea-109">需求</span><span class="sxs-lookup"><span data-stu-id="6dfea-109">Requirements</span></span>  
 <span data-ttu-id="6dfea-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="6dfea-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfea-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dfea-111">See also</span></span>

- [<span data-ttu-id="6dfea-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="6dfea-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
