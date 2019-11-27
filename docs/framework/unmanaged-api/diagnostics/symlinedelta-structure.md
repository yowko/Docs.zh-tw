---
title: SYMLINEDELTA 結構
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: a1e83e4b8cb6603029f3b42b1a3b9ba4810c9039
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438007"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="3a447-102">SYMLINEDELTA 結構</span><span class="sxs-lookup"><span data-stu-id="3a447-102">SYMLINEDELTA Structure</span></span>
<span data-ttu-id="3a447-103">提供相關資訊給符號處理常式，而這些方法是因編輯結果而移動。</span><span class="sxs-lookup"><span data-stu-id="3a447-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a447-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a447-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="3a447-105">Members</span><span class="sxs-lookup"><span data-stu-id="3a447-105">Members</span></span>  
  
|<span data-ttu-id="3a447-106">成員</span><span class="sxs-lookup"><span data-stu-id="3a447-106">Member</span></span>|<span data-ttu-id="3a447-107">描述</span><span class="sxs-lookup"><span data-stu-id="3a447-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="3a447-108">方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="3a447-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="3a447-109">方法已移動的行數。</span><span class="sxs-lookup"><span data-stu-id="3a447-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a447-110">需求</span><span class="sxs-lookup"><span data-stu-id="3a447-110">Requirements</span></span>  
 <span data-ttu-id="3a447-111">**標頭：** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="3a447-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a447-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3a447-112">See also</span></span>

- [<span data-ttu-id="3a447-113">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="3a447-113">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
