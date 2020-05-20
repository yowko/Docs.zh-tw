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
ms.openlocfilehash: 70ee853ff657a75dcc4df1454c4354f9d3f8202f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614717"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="dffbb-102">ISymUnmanagedWriter2::DefineConstant2 方法</span><span class="sxs-lookup"><span data-stu-id="dffbb-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="dffbb-103">定義常數值的名稱。</span><span class="sxs-lookup"><span data-stu-id="dffbb-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffbb-104">語法</span><span class="sxs-lookup"><span data-stu-id="dffbb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dffbb-105">參數</span><span class="sxs-lookup"><span data-stu-id="dffbb-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="dffbb-106">在常數名稱。</span><span class="sxs-lookup"><span data-stu-id="dffbb-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="dffbb-107">在常數的值。</span><span class="sxs-lookup"><span data-stu-id="dffbb-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="dffbb-108">在常數的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="dffbb-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dffbb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="dffbb-109">Return Value</span></span>  
 <span data-ttu-id="dffbb-110">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="dffbb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dffbb-111">需求</span><span class="sxs-lookup"><span data-stu-id="dffbb-111">Requirements</span></span>  
 <span data-ttu-id="dffbb-112">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="dffbb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffbb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dffbb-113">See also</span></span>

- [<span data-ttu-id="dffbb-114">ISymUnmanagedWriter2 介面</span><span class="sxs-lookup"><span data-stu-id="dffbb-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="dffbb-115">DefineConstant 方法</span><span class="sxs-lookup"><span data-stu-id="dffbb-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
