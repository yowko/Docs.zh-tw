---
title: ISymUnmanagedVariable::GetAddressField3 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: ff888d3e2b86efeea3f4e3d33528f731d85886bf
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615263"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="e4b6d-102">ISymUnmanagedVariable::GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="e4b6d-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="e4b6d-103">取得這個變數的第三個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="e4b6d-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="e4b6d-104">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="e4b6d-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b6d-105">語法</span><span class="sxs-lookup"><span data-stu-id="e4b6d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4b6d-106">參數</span><span class="sxs-lookup"><span data-stu-id="e4b6d-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e4b6d-107">脫銷`ULONG32`接收第三個位址欄位之的指標。</span><span class="sxs-lookup"><span data-stu-id="e4b6d-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4b6d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e4b6d-108">Return Value</span></span>  
 <span data-ttu-id="e4b6d-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="e4b6d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4b6d-110">需求</span><span class="sxs-lookup"><span data-stu-id="e4b6d-110">Requirements</span></span>  
 <span data-ttu-id="e4b6d-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="e4b6d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b6d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4b6d-112">See also</span></span>

- [<span data-ttu-id="e4b6d-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="e4b6d-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="e4b6d-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="e4b6d-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="e4b6d-115">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="e4b6d-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="e4b6d-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="e4b6d-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
