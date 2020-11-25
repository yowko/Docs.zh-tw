---
title: ISymUnmanagedScope::GetLocalCount 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 07c41e9d80b1703e86ae06525d64bf166ef2cf8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717548"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="12824-102">ISymUnmanagedScope::GetLocalCount 方法</span><span class="sxs-lookup"><span data-stu-id="12824-102">ISymUnmanagedScope::GetLocalCount Method</span></span>

<span data-ttu-id="12824-103">取得在此範圍內定義的區域變數計數。</span><span class="sxs-lookup"><span data-stu-id="12824-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12824-104">語法</span><span class="sxs-lookup"><span data-stu-id="12824-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12824-105">參數</span><span class="sxs-lookup"><span data-stu-id="12824-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="12824-106">擴展的指標，可 `ULONG32` 接收區域變數的計數。</span><span class="sxs-lookup"><span data-stu-id="12824-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12824-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="12824-107">Return Value</span></span>  

 <span data-ttu-id="12824-108">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="12824-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12824-109">需求</span><span class="sxs-lookup"><span data-stu-id="12824-109">Requirements</span></span>  

 <span data-ttu-id="12824-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="12824-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12824-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12824-111">See also</span></span>

- [<span data-ttu-id="12824-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="12824-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
