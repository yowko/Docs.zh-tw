---
title: CorSymAddrKind 列舉
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba24f5394ef8fb31d8bfa4e74ac59e7bd4af86d8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769872"
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="14adb-102">CorSymAddrKind 列舉</span><span class="sxs-lookup"><span data-stu-id="14adb-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="14adb-103">指出記憶體位址的類型。</span><span class="sxs-lookup"><span data-stu-id="14adb-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14adb-104">語法</span><span class="sxs-lookup"><span data-stu-id="14adb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="14adb-105">成員</span><span class="sxs-lookup"><span data-stu-id="14adb-105">Members</span></span>  
  
|<span data-ttu-id="14adb-106">成員</span><span class="sxs-lookup"><span data-stu-id="14adb-106">Member</span></span>|<span data-ttu-id="14adb-107">描述</span><span class="sxs-lookup"><span data-stu-id="14adb-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="14adb-108">表示 Microsoft intermediate language (MSIL) 本機變數或參數索引。</span><span class="sxs-lookup"><span data-stu-id="14adb-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="14adb-109">表示有相對虛擬位址到模組。</span><span class="sxs-lookup"><span data-stu-id="14adb-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="14adb-110">表示 CPU 暫存器。</span><span class="sxs-lookup"><span data-stu-id="14adb-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="14adb-111">表示第一個的位址是暫存器，而且第二個位址是位移。</span><span class="sxs-lookup"><span data-stu-id="14adb-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="14adb-112">表示基底的位址位移。</span><span class="sxs-lookup"><span data-stu-id="14adb-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="14adb-113">表示第一個位址是暫存器、 低部分，而且第二個位址是高的部分。</span><span class="sxs-lookup"><span data-stu-id="14adb-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="14adb-114">表示第一個的位址是暫存器的低部分，第二個是高的部分，第三個是位移。</span><span class="sxs-lookup"><span data-stu-id="14adb-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="14adb-115">表示第一個的位址是暫存器、 第二個是表示的位移和第三個是暫存器的高部分。</span><span class="sxs-lookup"><span data-stu-id="14adb-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="14adb-116">表示第一個位址是欄位的開頭，而且第二個位址是欄位長度。</span><span class="sxs-lookup"><span data-stu-id="14adb-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="14adb-117">表示第一個位址是區段，而且第二個位址是位移。</span><span class="sxs-lookup"><span data-stu-id="14adb-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14adb-118">需求</span><span class="sxs-lookup"><span data-stu-id="14adb-118">Requirements</span></span>  
 <span data-ttu-id="14adb-119">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="14adb-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14adb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14adb-120">See also</span></span>

- [<span data-ttu-id="14adb-121">診斷符號存放區列舉</span><span class="sxs-lookup"><span data-stu-id="14adb-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
