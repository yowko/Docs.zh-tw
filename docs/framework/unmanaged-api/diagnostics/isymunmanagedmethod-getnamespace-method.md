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
ms.openlocfilehash: 7e26c272ee1ecf03f7d2a347cf7ca2cc3efa2122
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699556"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="8bfdf-102">ISymUnmanagedMethod::GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="8bfdf-102">ISymUnmanagedMethod::GetNamespace Method</span></span>

<span data-ttu-id="8bfdf-103">取得在其中定義此方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="8bfdf-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bfdf-104">語法</span><span class="sxs-lookup"><span data-stu-id="8bfdf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bfdf-105">參數</span><span class="sxs-lookup"><span data-stu-id="8bfdf-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8bfdf-106">擴展設定為傳回之 [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="8bfdf-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bfdf-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="8bfdf-107">Return Value</span></span>  

 <span data-ttu-id="8bfdf-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8bfdf-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bfdf-109">需求</span><span class="sxs-lookup"><span data-stu-id="8bfdf-109">Requirements</span></span>  

 <span data-ttu-id="8bfdf-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8bfdf-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bfdf-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bfdf-111">See also</span></span>

- [<span data-ttu-id="8bfdf-112">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="8bfdf-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
