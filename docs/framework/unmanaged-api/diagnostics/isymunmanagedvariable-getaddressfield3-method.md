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
ms.openlocfilehash: 13746c4ac6322a401e547c1c7acc99c0eda9accf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723333"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="ee1df-102">ISymUnmanagedVariable::GetAddressField3 方法</span><span class="sxs-lookup"><span data-stu-id="ee1df-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>

<span data-ttu-id="ee1df-103">取得這個變數的第三個位址欄位。</span><span class="sxs-lookup"><span data-stu-id="ee1df-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="ee1df-104">其意義取決於位址的種類。</span><span class="sxs-lookup"><span data-stu-id="ee1df-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee1df-105">語法</span><span class="sxs-lookup"><span data-stu-id="ee1df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee1df-106">參數</span><span class="sxs-lookup"><span data-stu-id="ee1df-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="ee1df-107">擴展 `ULONG32` 接收第三個位址欄位之的指標。</span><span class="sxs-lookup"><span data-stu-id="ee1df-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee1df-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ee1df-108">Return Value</span></span>  

 <span data-ttu-id="ee1df-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ee1df-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee1df-110">需求</span><span class="sxs-lookup"><span data-stu-id="ee1df-110">Requirements</span></span>  

 <span data-ttu-id="ee1df-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ee1df-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee1df-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee1df-112">See also</span></span>

- [<span data-ttu-id="ee1df-113">ISymUnmanagedVariable 介面</span><span class="sxs-lookup"><span data-stu-id="ee1df-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="ee1df-114">GetAddressField1 方法</span><span class="sxs-lookup"><span data-stu-id="ee1df-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="ee1df-115">GetAddressField2 方法</span><span class="sxs-lookup"><span data-stu-id="ee1df-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="ee1df-116">GetAddressKind 方法</span><span class="sxs-lookup"><span data-stu-id="ee1df-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
