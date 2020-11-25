---
title: CorSymVarFlag 列舉
ms.date: 03/30/2017
api_name:
- CorSymVarFlag
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymVarFlag
helpviewer_keywords:
- CorSymVarFlag enumeration [.NET Framework debugging]
ms.assetid: c3f7d307-4047-4f9a-be8c-f152fca42fd0
topic_type:
- apiref
ms.openlocfilehash: ed08d9f818f6fc180dbd655243488bf8a527ae11
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725283"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="1cc34-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="1cc34-102">CorSymVarFlag Enumeration</span></span>

<span data-ttu-id="1cc34-103">指出變數是否為編譯器產生的。</span><span class="sxs-lookup"><span data-stu-id="1cc34-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc34-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cc34-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="1cc34-105">成員</span><span class="sxs-lookup"><span data-stu-id="1cc34-105">Members</span></span>  
  
|<span data-ttu-id="1cc34-106">member</span><span class="sxs-lookup"><span data-stu-id="1cc34-106">Member</span></span>|<span data-ttu-id="1cc34-107">描述</span><span class="sxs-lookup"><span data-stu-id="1cc34-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="1cc34-108">表示指定的變數是編譯器產生的。</span><span class="sxs-lookup"><span data-stu-id="1cc34-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1cc34-109">需求</span><span class="sxs-lookup"><span data-stu-id="1cc34-109">Requirements</span></span>  

 <span data-ttu-id="1cc34-110">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="1cc34-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc34-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cc34-111">See also</span></span>

- [<span data-ttu-id="1cc34-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="1cc34-112">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
