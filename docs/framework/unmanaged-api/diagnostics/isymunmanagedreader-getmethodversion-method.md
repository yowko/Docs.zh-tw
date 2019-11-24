---
title: ISymUnmanagedReader::GetMethodVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: fcaf748413321f684336543e60f735af69894b51
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436005"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="6fa10-102">ISymUnmanagedReader::GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="6fa10-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="6fa10-103">Gets the method version.</span><span class="sxs-lookup"><span data-stu-id="6fa10-103">Gets the method version.</span></span> <span data-ttu-id="6fa10-104">The method version starts at 1 and is incremented each time the method is recompiled.</span><span class="sxs-lookup"><span data-stu-id="6fa10-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="6fa10-105">Recompilation can happen without changes to the method.</span><span class="sxs-lookup"><span data-stu-id="6fa10-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa10-106">語法</span><span class="sxs-lookup"><span data-stu-id="6fa10-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fa10-107">參數</span><span class="sxs-lookup"><span data-stu-id="6fa10-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="6fa10-108">[in] The method for which to get the version.</span><span class="sxs-lookup"><span data-stu-id="6fa10-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="6fa10-109">[out] A pointer to a variable that receives the method version.</span><span class="sxs-lookup"><span data-stu-id="6fa10-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fa10-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="6fa10-110">Return Value</span></span>  
 <span data-ttu-id="6fa10-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="6fa10-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fa10-112">需求</span><span class="sxs-lookup"><span data-stu-id="6fa10-112">Requirements</span></span>  
 <span data-ttu-id="6fa10-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6fa10-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa10-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fa10-114">See also</span></span>

- [<span data-ttu-id="6fa10-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="6fa10-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
