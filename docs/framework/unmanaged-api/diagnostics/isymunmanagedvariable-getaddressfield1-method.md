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
ms.openlocfilehash: 253fd17178c03bc0c4d8ea031888a404ad56f876
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615276"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="c44b9-102">ISymUnmanagedVariable::GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="c44b9-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="c44b9-103">取得這個變數的第一個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="c44b9-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="c44b9-104">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="c44b9-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c44b9-105">語法</span><span class="sxs-lookup"><span data-stu-id="c44b9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c44b9-106">參數</span><span class="sxs-lookup"><span data-stu-id="c44b9-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c44b9-107">脫銷`ULONG32`接收第一個位址欄位之的指標。</span><span class="sxs-lookup"><span data-stu-id="c44b9-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c44b9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="c44b9-108">Return Value</span></span>  
 <span data-ttu-id="c44b9-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c44b9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c44b9-110">需求</span><span class="sxs-lookup"><span data-stu-id="c44b9-110">Requirements</span></span>  
 <span data-ttu-id="c44b9-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="c44b9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44b9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c44b9-112">See also</span></span>

- [<span data-ttu-id="c44b9-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="c44b9-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="c44b9-114">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="c44b9-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="c44b9-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="c44b9-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="c44b9-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="c44b9-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
