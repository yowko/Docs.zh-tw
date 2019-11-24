---
title: AssemblyAttributesGoHere Class (System.Runtime.CompilerServices)
ms.date: 03/30/2017
api_name:
- System.Runtime.CompilerServices.AssemblyAttributesGoHere
api_location:
- mscorlib.dll
api_type:
- Assembly
f1_keywords:
- AssemblyAttributesGoHere
helpviewer_keywords:
- AssemblyAttributesGoHere type
- Alink API, AssemblyAttributesGoHere type
ms.assetid: 7b26fcb6-94f4-4f09-933e-b33efe451f4f
topic_type:
- apiref
ms.openlocfilehash: 99d7d2bbbb0586db34b5cb7a785b0448a20ab5bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446648"
---
# <a name="assemblyattributesgohere-class"></a><span data-ttu-id="ebe08-102">AssemblyAttributesGoHere Class</span><span class="sxs-lookup"><span data-stu-id="ebe08-102">AssemblyAttributesGoHere Class</span></span>

<span data-ttu-id="ebe08-103">供 ALink 用來做為儲存自訂屬性相關資訊的預留位置。</span><span class="sxs-lookup"><span data-stu-id="ebe08-103">Used by ALink as a placeholder to store information about custom attributes.</span></span>

## <a name="syntax"></a><span data-ttu-id="ebe08-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebe08-104">Syntax</span></span>

```csharp
internal sealed class AssemblyAttributesGoHere
```

## <a name="remarks"></a><span data-ttu-id="ebe08-105">備註</span><span class="sxs-lookup"><span data-stu-id="ebe08-105">Remarks</span></span>

<span data-ttu-id="ebe08-106">這個類型的參考可能會內嵌在來源中包含組件自訂屬性的 netmodule 中。</span><span class="sxs-lookup"><span data-stu-id="ebe08-106">References to this type might be embedded inside netmodules whose sources contain assembly custom attributes.</span></span> <span data-ttu-id="ebe08-107">從一個或多個包含這些類型參考的 netmodule 建置組件資訊清單時，ALink 會使用附加至這些參考的資訊來發出真正的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="ebe08-107">When building an assembly manifest from one or more netmodules that contain references to these types, ALink uses information attached to these references to emit real custom attributes.</span></span> <span data-ttu-id="ebe08-108">因此，這個類型永遠不會具現化，而其參考只會用來做為建置流程的一部分，在最後的組件中並沒有任何用途。</span><span class="sxs-lookup"><span data-stu-id="ebe08-108">As such, this type is never instantiated, and references to it are used only as part of the build process and serve no purpose in the final assembly.</span></span>

<span data-ttu-id="ebe08-109">這個類型的參考會指出與安全性無關且不是多用途的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="ebe08-109">References to this type indicate custom attributes that are not security related and are not multiple-use.</span></span>

<span data-ttu-id="ebe08-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span><span class="sxs-lookup"><span data-stu-id="ebe08-110">These types are marked "internal" within the .NET Framework and are located in the <xref:System.Runtime.CompilerServices> namespace.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebe08-111">需求</span><span class="sxs-lookup"><span data-stu-id="ebe08-111">Requirements</span></span>

<span data-ttu-id="ebe08-112">mscorlib.dll</span><span class="sxs-lookup"><span data-stu-id="ebe08-112">mscorlib.dll</span></span>

## <a name="see-also"></a><span data-ttu-id="ebe08-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="ebe08-113">See also</span></span>

- [<span data-ttu-id="ebe08-114">AssemblyAttributesGoHereM</span><span class="sxs-lookup"><span data-stu-id="ebe08-114">AssemblyAttributesGoHereM</span></span>](assemblyattributesgoherem.md)
- [<span data-ttu-id="ebe08-115">AssemblyAttributesGoHereS</span><span class="sxs-lookup"><span data-stu-id="ebe08-115">AssemblyAttributesGoHereS</span></span>](assemblyattributesgoheres.md)
- [<span data-ttu-id="ebe08-116">AssemblyAttributesGoHereSM</span><span class="sxs-lookup"><span data-stu-id="ebe08-116">AssemblyAttributesGoHereSM</span></span>](assemblyattributesgoheresm.md)
