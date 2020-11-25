---
title: ISymUnmanagedVariable::GetAddressField2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
ms.openlocfilehash: 858341d5b8b1b3ecbe9dd5bd39a38f9cfd0d08dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714168"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="d5836-102">ISymUnmanagedVariable::GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="d5836-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>

<span data-ttu-id="d5836-103">取得這個變數的第二個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="d5836-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="d5836-104">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="d5836-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5836-105">語法</span><span class="sxs-lookup"><span data-stu-id="d5836-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5836-106">參數</span><span class="sxs-lookup"><span data-stu-id="d5836-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d5836-107">擴展 `ULONG32` 接收第二個位址欄位之的指標。</span><span class="sxs-lookup"><span data-stu-id="d5836-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5836-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d5836-108">Return Value</span></span>  

 <span data-ttu-id="d5836-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d5836-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5836-110">需求</span><span class="sxs-lookup"><span data-stu-id="d5836-110">Requirements</span></span>  

 <span data-ttu-id="d5836-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="d5836-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5836-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5836-112">See also</span></span>

- [<span data-ttu-id="d5836-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="d5836-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="d5836-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="d5836-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="d5836-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="d5836-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="d5836-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="d5836-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
