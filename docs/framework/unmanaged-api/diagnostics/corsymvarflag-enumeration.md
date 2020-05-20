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
ms.openlocfilehash: d41e048b67d4bc7159f6dd5266457651f1658290
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420587"
---
# <a name="corsymvarflag-enumeration"></a><span data-ttu-id="0df5e-102">CorSymVarFlag 列舉</span><span class="sxs-lookup"><span data-stu-id="0df5e-102">CorSymVarFlag Enumeration</span></span>
<span data-ttu-id="0df5e-103">指出變數是否由編譯器產生。</span><span class="sxs-lookup"><span data-stu-id="0df5e-103">Indicates whether a variable is compiler-generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0df5e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymVarFlag
{  
    VAR_IS_COMP_GEN = 1  
} CorSymVarFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="0df5e-105">成員</span><span class="sxs-lookup"><span data-stu-id="0df5e-105">Members</span></span>  
  
|<span data-ttu-id="0df5e-106">成員</span><span class="sxs-lookup"><span data-stu-id="0df5e-106">Member</span></span>|<span data-ttu-id="0df5e-107">說明</span><span class="sxs-lookup"><span data-stu-id="0df5e-107">Description</span></span>|  
|------------|-----------------|  
|`VAR_IS_COMP_GEN`|<span data-ttu-id="0df5e-108">表示指定的變數是編譯器產生的。</span><span class="sxs-lookup"><span data-stu-id="0df5e-108">Indicates that the given variable is compiler-generated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0df5e-109">需求</span><span class="sxs-lookup"><span data-stu-id="0df5e-109">Requirements</span></span>  
 <span data-ttu-id="0df5e-110">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="0df5e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df5e-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0df5e-111">See also</span></span>

- [<span data-ttu-id="0df5e-112">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="0df5e-112">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
