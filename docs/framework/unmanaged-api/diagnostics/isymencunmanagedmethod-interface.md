---
title: ISymENCUnmanagedMethod 介面
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441873"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="9da96-102">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="9da96-102">ISymENCUnmanagedMethod Interface</span></span>
<span data-ttu-id="9da96-103">提供 [編輯後繼續] 功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="9da96-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9da96-104">方法</span><span class="sxs-lookup"><span data-stu-id="9da96-104">Methods</span></span>  
  
|<span data-ttu-id="9da96-105">方法</span><span class="sxs-lookup"><span data-stu-id="9da96-105">Method</span></span>|<span data-ttu-id="9da96-106">描述</span><span class="sxs-lookup"><span data-stu-id="9da96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9da96-107">GetDocumentsForMethod 方法</span><span class="sxs-lookup"><span data-stu-id="9da96-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="9da96-108">取得此方法在中具有行的檔。</span><span class="sxs-lookup"><span data-stu-id="9da96-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="9da96-109">GetDocumentsForMethodCount 方法</span><span class="sxs-lookup"><span data-stu-id="9da96-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="9da96-110">取得此方法在中具有行的檔數目。</span><span class="sxs-lookup"><span data-stu-id="9da96-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="9da96-111">GetFileNameFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9da96-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="9da96-112">取得與位移相關聯之行的檔案名。</span><span class="sxs-lookup"><span data-stu-id="9da96-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="9da96-113">GetLineFromOffset 方法</span><span class="sxs-lookup"><span data-stu-id="9da96-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="9da96-114">取得與位移相關聯的線條資訊。</span><span class="sxs-lookup"><span data-stu-id="9da96-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="9da96-115">GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="9da96-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="9da96-116">取得特定檔中方法的最小起始行和最大結尾行。</span><span class="sxs-lookup"><span data-stu-id="9da96-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9da96-117">需求</span><span class="sxs-lookup"><span data-stu-id="9da96-117">Requirements</span></span>  
 <span data-ttu-id="9da96-118">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="9da96-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9da96-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9da96-119">See also</span></span>

- [<span data-ttu-id="9da96-120">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="9da96-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
