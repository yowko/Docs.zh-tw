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
ms.openlocfilehash: 4ac1fc0b3567c49dfb36d2886926bee72d62a8dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446073"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="99c69-102">ISymUnmanagedVariable::GetEndOffset 方法</span><span class="sxs-lookup"><span data-stu-id="99c69-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="99c69-103">取得這個變數在其父系內的結束位移。</span><span class="sxs-lookup"><span data-stu-id="99c69-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="99c69-104">如果這是範圍內的本機變數，則結束位移會落在為範圍定義的位移內。</span><span class="sxs-lookup"><span data-stu-id="99c69-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c69-105">語法</span><span class="sxs-lookup"><span data-stu-id="99c69-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99c69-106">參數</span><span class="sxs-lookup"><span data-stu-id="99c69-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="99c69-107">脫銷接收結束位移之 `ULONG32` 的指標。</span><span class="sxs-lookup"><span data-stu-id="99c69-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99c69-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="99c69-108">Return Value</span></span>  
 <span data-ttu-id="99c69-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="99c69-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99c69-110">需求</span><span class="sxs-lookup"><span data-stu-id="99c69-110">Requirements</span></span>  
 <span data-ttu-id="99c69-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="99c69-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c69-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99c69-112">See also</span></span>

- [<span data-ttu-id="99c69-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="99c69-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="99c69-114">GetStartOffset 方法</span><span class="sxs-lookup"><span data-stu-id="99c69-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
