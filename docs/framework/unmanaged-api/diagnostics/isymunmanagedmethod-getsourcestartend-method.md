---
title: ISymUnmanagedMethod::GetSourceStartEnd 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
ms.openlocfilehash: 01ab69b73a7bc4929e2ebd49b3847f8d7c4646a2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448859"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="296b8-102">ISymUnmanagedMethod::GetSourceStartEnd 方法</span><span class="sxs-lookup"><span data-stu-id="296b8-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="296b8-103">Gets the start and end document positions for the source of this method.</span><span class="sxs-lookup"><span data-stu-id="296b8-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="296b8-104">The first array position is the start, and the second array position is the end.</span><span class="sxs-lookup"><span data-stu-id="296b8-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="296b8-105">語法</span><span class="sxs-lookup"><span data-stu-id="296b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="296b8-106">參數</span><span class="sxs-lookup"><span data-stu-id="296b8-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="296b8-107">[in] The starting and ending source documents.</span><span class="sxs-lookup"><span data-stu-id="296b8-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="296b8-108">[in] The starting and ending lines in the corresponding source documents.</span><span class="sxs-lookup"><span data-stu-id="296b8-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="296b8-109">[in] The starting and ending columns in the corresponding source documents.</span><span class="sxs-lookup"><span data-stu-id="296b8-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="296b8-110">[out] `true` if positions were defined; otherwise, `false`.</span><span class="sxs-lookup"><span data-stu-id="296b8-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="296b8-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="296b8-111">Return Value</span></span>  
 <span data-ttu-id="296b8-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="296b8-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="296b8-113">需求</span><span class="sxs-lookup"><span data-stu-id="296b8-113">Requirements</span></span>  
 <span data-ttu-id="296b8-114">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="296b8-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296b8-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="296b8-115">See also</span></span>

- [<span data-ttu-id="296b8-116">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="296b8-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
