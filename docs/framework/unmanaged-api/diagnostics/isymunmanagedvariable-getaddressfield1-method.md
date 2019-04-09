---
title: ISymUnmanagedVariable::GetAddressField1 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67634024b04e82aa3a3c0b96dc260114c4c16371
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179695"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="5d65a-102">ISymUnmanagedVariable::GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="5d65a-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="5d65a-103">取得這個變數中的第一個 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="5d65a-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="5d65a-104">其意義取決於位址的類型。</span><span class="sxs-lookup"><span data-stu-id="5d65a-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d65a-105">語法</span><span class="sxs-lookup"><span data-stu-id="5d65a-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d65a-106">參數</span><span class="sxs-lookup"><span data-stu-id="5d65a-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5d65a-107">[out]指標`ULONG32`接收第一個 [位址] 欄位。</span><span class="sxs-lookup"><span data-stu-id="5d65a-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d65a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="5d65a-108">Return Value</span></span>  
 <span data-ttu-id="5d65a-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d65a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d65a-110">需求</span><span class="sxs-lookup"><span data-stu-id="5d65a-110">Requirements</span></span>  
 <span data-ttu-id="5d65a-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5d65a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d65a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d65a-112">See also</span></span>

- [<span data-ttu-id="5d65a-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="5d65a-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="5d65a-114">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="5d65a-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="5d65a-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="5d65a-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="5d65a-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="5d65a-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
