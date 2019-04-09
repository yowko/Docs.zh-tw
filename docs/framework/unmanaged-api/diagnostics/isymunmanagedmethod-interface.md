---
title: ISymUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c29656a4787c674886505a3be2508470460dfc10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136522"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="ade47-102">ISymUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="ade47-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="ade47-103">代表符號存放區內的方法。</span><span class="sxs-lookup"><span data-stu-id="ade47-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="ade47-104">這個介面會提供屬性的權限只與符號相關的方法，而不是型別相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="ade47-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ade47-105">方法</span><span class="sxs-lookup"><span data-stu-id="ade47-105">Methods</span></span>  
  
|<span data-ttu-id="ade47-106">方法</span><span class="sxs-lookup"><span data-stu-id="ade47-106">Method</span></span>|<span data-ttu-id="ade47-107">描述</span><span class="sxs-lookup"><span data-stu-id="ade47-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ade47-108">GetNamespace 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="ade47-109">取得這個方法會在其中定義的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ade47-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="ade47-110">GetOffset 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="ade47-111">文件中的指定位置傳回此對應的方法中的位移。</span><span class="sxs-lookup"><span data-stu-id="ade47-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="ade47-112">GetParameters 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="ade47-113">取得這個方法的參數。</span><span class="sxs-lookup"><span data-stu-id="ade47-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="ade47-114">GetRanges 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="ade47-115">指定的文件中的位置，傳回陣列的開始和結束位移組對應的 Microsoft intermediate language (MSIL，其中涵蓋在這個方法內的位置) 範圍。</span><span class="sxs-lookup"><span data-stu-id="ade47-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="ade47-116">GetRootScope 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="ade47-117">取得這個方法內的根語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="ade47-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="ade47-118">這個範圍會封入整個方法。</span><span class="sxs-lookup"><span data-stu-id="ade47-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="ade47-119">GetScopeFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="ade47-120">取得包含指定的位移這個方法內的最封入語彙範圍。</span><span class="sxs-lookup"><span data-stu-id="ade47-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="ade47-121">GetSequencePointCount 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="ade47-122">取得這個方法內的序列點的計數。</span><span class="sxs-lookup"><span data-stu-id="ade47-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="ade47-123">GetSequencePoints 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="ade47-124">取得這個方法內的所有序列點。</span><span class="sxs-lookup"><span data-stu-id="ade47-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="ade47-125">GetSourceStartEnd 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="ade47-126">取得這個方法的來源的開始和結束文件位置。</span><span class="sxs-lookup"><span data-stu-id="ade47-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="ade47-127">GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="ade47-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="ade47-128">傳回此方法的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ade47-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ade47-129">需求</span><span class="sxs-lookup"><span data-stu-id="ade47-129">Requirements</span></span>  
 <span data-ttu-id="ade47-130">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ade47-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade47-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade47-131">See also</span></span>

- [<span data-ttu-id="ade47-132">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="ade47-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
