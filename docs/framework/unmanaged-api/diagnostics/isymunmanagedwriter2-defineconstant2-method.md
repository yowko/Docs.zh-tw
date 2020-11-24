---
title: ISymUnmanagedWriter2::DefineConstant2 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: d45ab56f081bf0a8802b17e338f7b404809f0f16
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683468"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="cb1a9-102">ISymUnmanagedWriter2::DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="cb1a9-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>

<span data-ttu-id="cb1a9-103">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="cb1a9-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb1a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb1a9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb1a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb1a9-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="cb1a9-106">在常數名稱。</span><span class="sxs-lookup"><span data-stu-id="cb1a9-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="cb1a9-107">在常數的值。</span><span class="sxs-lookup"><span data-stu-id="cb1a9-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="cb1a9-108">在常數的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="cb1a9-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb1a9-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="cb1a9-109">Return Value</span></span>  

 <span data-ttu-id="cb1a9-110">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cb1a9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb1a9-111">需求</span><span class="sxs-lookup"><span data-stu-id="cb1a9-111">Requirements</span></span>  

 <span data-ttu-id="cb1a9-112">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="cb1a9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb1a9-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb1a9-113">See also</span></span>

- [<span data-ttu-id="cb1a9-114">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="cb1a9-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="cb1a9-115">DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="cb1a9-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
