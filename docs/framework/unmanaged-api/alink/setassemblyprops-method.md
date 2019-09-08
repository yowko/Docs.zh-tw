---
title: SetAssemblyProps 方法
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyProps
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 180eb1a3129cfcd96668ecfee11947c15c5e0915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776908"
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="548b4-102">SetAssemblyProps 方法</span><span class="sxs-lookup"><span data-stu-id="548b4-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="548b4-103">指派元件層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="548b4-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="548b4-104">語法</span><span class="sxs-lookup"><span data-stu-id="548b4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="548b4-105">參數</span><span class="sxs-lookup"><span data-stu-id="548b4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="548b4-106">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="548b4-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="548b4-107">定義屬性的檔案。</span><span class="sxs-lookup"><span data-stu-id="548b4-107">File that defines the property.</span></span> <span data-ttu-id="548b4-108">如果未指出未`AssemblyID`系結的 .netmodule，則可以是 Null。</span><span class="sxs-lookup"><span data-stu-id="548b4-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="548b4-109">表示要修改的選項。</span><span class="sxs-lookup"><span data-stu-id="548b4-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="548b4-110">選項的新值。</span><span class="sxs-lookup"><span data-stu-id="548b4-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="548b4-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="548b4-111">Return Value</span></span>  
 <span data-ttu-id="548b4-112">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="548b4-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="548b4-113">需求</span><span class="sxs-lookup"><span data-stu-id="548b4-113">Requirements</span></span>  
 <span data-ttu-id="548b4-114">需要 alink. h。</span><span class="sxs-lookup"><span data-stu-id="548b4-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548b4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="548b4-115">See also</span></span>

- [<span data-ttu-id="548b4-116">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="548b4-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="548b4-117">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="548b4-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="548b4-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="548b4-118">ALink API</span></span>](index.md)
