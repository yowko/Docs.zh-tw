---
title: ISymUnmanagedMethod::GetOffset 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 358f3d3d7c231a2baa9d2c467935ba3a5867e36b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614470"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="975d3-102">ISymUnmanagedMethod::GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="975d3-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="975d3-103">傳回這個方法內對應于檔內指定位置的位移。</span><span class="sxs-lookup"><span data-stu-id="975d3-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="975d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="975d3-105">參數</span><span class="sxs-lookup"><span data-stu-id="975d3-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="975d3-106">在要求位移之檔的指標。</span><span class="sxs-lookup"><span data-stu-id="975d3-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="975d3-107">在要求位移的檔行。</span><span class="sxs-lookup"><span data-stu-id="975d3-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="975d3-108">在要求位移的檔資料行。</span><span class="sxs-lookup"><span data-stu-id="975d3-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="975d3-109">脫銷接收位移之的指標 `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="975d3-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="975d3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="975d3-110">Return Value</span></span>  
 <span data-ttu-id="975d3-111">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="975d3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975d3-112">需求</span><span class="sxs-lookup"><span data-stu-id="975d3-112">Requirements</span></span>  
 <span data-ttu-id="975d3-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="975d3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975d3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="975d3-114">See also</span></span>

- [<span data-ttu-id="975d3-115">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="975d3-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
