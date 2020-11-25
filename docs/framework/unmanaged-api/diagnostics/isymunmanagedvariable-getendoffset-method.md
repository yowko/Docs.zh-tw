---
title: ISymUnmanagedVariable::GetEndOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: cf4179f839b62409d5b2185f3e11e8e732c29187
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721864"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="3dcc3-102">ISymUnmanagedVariable::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="3dcc3-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>

<span data-ttu-id="3dcc3-103">取得此變數在其父系內的結束位移。</span><span class="sxs-lookup"><span data-stu-id="3dcc3-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="3dcc3-104">如果這是範圍內的區域變數，結束位移將落在為範圍定義的位移內。</span><span class="sxs-lookup"><span data-stu-id="3dcc3-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dcc3-105">語法</span><span class="sxs-lookup"><span data-stu-id="3dcc3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dcc3-106">參數</span><span class="sxs-lookup"><span data-stu-id="3dcc3-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="3dcc3-107">擴展的指標，可 `ULONG32` 接收結束位移。</span><span class="sxs-lookup"><span data-stu-id="3dcc3-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dcc3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3dcc3-108">Return Value</span></span>  

 <span data-ttu-id="3dcc3-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="3dcc3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dcc3-110">需求</span><span class="sxs-lookup"><span data-stu-id="3dcc3-110">Requirements</span></span>  

 <span data-ttu-id="3dcc3-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3dcc3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcc3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3dcc3-112">See also</span></span>

- [<span data-ttu-id="3dcc3-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="3dcc3-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="3dcc3-114">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="3dcc3-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
