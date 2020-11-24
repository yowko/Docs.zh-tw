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
ms.openlocfilehash: dd45703540f8dc41b746ca03b4f09d74186aa9aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690937"
---
# <a name="symlinedelta-structure"></a><span data-ttu-id="c6e92-102">SYMLINEDELTA 結構</span><span class="sxs-lookup"><span data-stu-id="c6e92-102">SYMLINEDELTA Structure</span></span>

<span data-ttu-id="c6e92-103">提供有關方法的符號處理常式資訊，這些方法是在編輯時移動的。</span><span class="sxs-lookup"><span data-stu-id="c6e92-103">Provides information to the symbol handler about methods that were moved as a result of edits.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e92-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6e92-104">Syntax</span></span>  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a><span data-ttu-id="c6e92-105">成員</span><span class="sxs-lookup"><span data-stu-id="c6e92-105">Members</span></span>  
  
|<span data-ttu-id="c6e92-106">member</span><span class="sxs-lookup"><span data-stu-id="c6e92-106">Member</span></span>|<span data-ttu-id="c6e92-107">描述</span><span class="sxs-lookup"><span data-stu-id="c6e92-107">Description</span></span>|  
|------------|-----------------|  
|`mdMethod`|<span data-ttu-id="c6e92-108">方法的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="c6e92-108">The method's metadata token.</span></span>|  
|`delta`|<span data-ttu-id="c6e92-109">移動方法的行數。</span><span class="sxs-lookup"><span data-stu-id="c6e92-109">The number of lines the method was moved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c6e92-110">需求</span><span class="sxs-lookup"><span data-stu-id="c6e92-110">Requirements</span></span>  

 <span data-ttu-id="c6e92-111">**標頭：** CorSym .idl</span><span class="sxs-lookup"><span data-stu-id="c6e92-111">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e92-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6e92-112">See also</span></span>

- [<span data-ttu-id="c6e92-113">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="c6e92-113">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
