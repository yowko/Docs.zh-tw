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
ms.openlocfilehash: 6256d052780b1c610e61267be2517954d722a42d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610596"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="27254-102">ISymUnmanagedVariable::GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="27254-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="27254-103">取得這個變數的第二個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="27254-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="27254-104">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="27254-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27254-105">語法</span><span class="sxs-lookup"><span data-stu-id="27254-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27254-106">參數</span><span class="sxs-lookup"><span data-stu-id="27254-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="27254-107">脫銷`ULONG32`接收第二個位址欄位之的指標。</span><span class="sxs-lookup"><span data-stu-id="27254-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27254-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="27254-108">Return Value</span></span>  
 <span data-ttu-id="27254-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="27254-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27254-110">需求</span><span class="sxs-lookup"><span data-stu-id="27254-110">Requirements</span></span>  
 <span data-ttu-id="27254-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="27254-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27254-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27254-112">See also</span></span>

- [<span data-ttu-id="27254-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="27254-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="27254-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="27254-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="27254-115">GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="27254-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="27254-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="27254-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
