---
title: ISymUnmanagedVariable::GetStartOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: 68d20c33c5ccd554554cae57ee55f6f51d5d980c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733304"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="8c230-102">ISymUnmanagedVariable::GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8c230-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>

<span data-ttu-id="8c230-103">取得此變數在其父系內的開始位移。</span><span class="sxs-lookup"><span data-stu-id="8c230-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="8c230-104">如果這是範圍內的區域變數，開始位移將落在為範圍定義的位移內。</span><span class="sxs-lookup"><span data-stu-id="8c230-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c230-105">語法</span><span class="sxs-lookup"><span data-stu-id="8c230-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c230-106">參數</span><span class="sxs-lookup"><span data-stu-id="8c230-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="8c230-107">擴展的指標，可 `ULONG32` 接收起始位移。</span><span class="sxs-lookup"><span data-stu-id="8c230-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c230-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8c230-108">Return Value</span></span>  

 <span data-ttu-id="8c230-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8c230-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c230-110">需求</span><span class="sxs-lookup"><span data-stu-id="8c230-110">Requirements</span></span>  

 <span data-ttu-id="8c230-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="8c230-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c230-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c230-112">See also</span></span>

- [<span data-ttu-id="8c230-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="8c230-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="8c230-114">GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="8c230-114">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
