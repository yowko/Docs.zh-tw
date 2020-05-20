---
title: ISymUnmanagedScope::GetEndOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 4d6bd239a15bd196f840007af120cb062499f4c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614847"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="d629c-102">ISymUnmanagedScope::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d629c-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="d629c-103">取得此範圍的結束位移。</span><span class="sxs-lookup"><span data-stu-id="d629c-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d629c-104">語法</span><span class="sxs-lookup"><span data-stu-id="d629c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d629c-105">參數</span><span class="sxs-lookup"><span data-stu-id="d629c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d629c-106">脫銷`ULONG32`接收結束位移之的指標。</span><span class="sxs-lookup"><span data-stu-id="d629c-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d629c-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="d629c-107">Return Value</span></span>  
 <span data-ttu-id="d629c-108">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d629c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d629c-109">需求</span><span class="sxs-lookup"><span data-stu-id="d629c-109">Requirements</span></span>  
 <span data-ttu-id="d629c-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d629c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d629c-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d629c-111">See also</span></span>

- [<span data-ttu-id="d629c-112">ISymUnmanagedScope 介面</span><span class="sxs-lookup"><span data-stu-id="d629c-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="d629c-113">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="d629c-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
