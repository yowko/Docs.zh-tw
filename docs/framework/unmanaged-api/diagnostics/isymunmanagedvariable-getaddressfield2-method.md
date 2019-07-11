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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463416165d2dbd7724d5cf0d29e40d8243ade34b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778314"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="fe010-102">ISymUnmanagedVariable::GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="fe010-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="fe010-103">取得這個變數中的第二個 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="fe010-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="fe010-104">其意義取決於位址的類型。</span><span class="sxs-lookup"><span data-stu-id="fe010-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe010-105">語法</span><span class="sxs-lookup"><span data-stu-id="fe010-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe010-106">參數</span><span class="sxs-lookup"><span data-stu-id="fe010-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fe010-107">[out]指標`ULONG32`接收第二個 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="fe010-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe010-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe010-108">Return Value</span></span>  
 <span data-ttu-id="fe010-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="fe010-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe010-110">需求</span><span class="sxs-lookup"><span data-stu-id="fe010-110">Requirements</span></span>  
 <span data-ttu-id="fe010-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fe010-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe010-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe010-112">See also</span></span>

- [<span data-ttu-id="fe010-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="fe010-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="fe010-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="fe010-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="fe010-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="fe010-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="fe010-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="fe010-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
