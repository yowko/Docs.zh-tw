---
title: MemoryStream. InternalGetOriginAndLength 方法（System.IO）
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d82b5080e9fbd5fc6603f1cddae996c75a06d3a3
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215467"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a><span data-ttu-id="7c17a-102">MemoryStream. InternalGetOriginAndLength 方法</span><span class="sxs-lookup"><span data-stu-id="7c17a-102">MemoryStream.InternalGetOriginAndLength method</span></span>

<span data-ttu-id="7c17a-103">取得記憶體資料流程來源和長度的內部值。</span><span class="sxs-lookup"><span data-stu-id="7c17a-103">Gets the internal values of origin and length of the memory stream.</span></span>

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a><span data-ttu-id="7c17a-104">參數</span><span class="sxs-lookup"><span data-stu-id="7c17a-104">Parameters</span></span>

- <span data-ttu-id="7c17a-105">`origin` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="7c17a-105">`origin` <xref:System.Int32></span></span>\
  <span data-ttu-id="7c17a-106">當這個方法傳回時，就是建立新的 <xref:System.IO.MemoryStream> 物件時，所指定之位元組陣列的位移。</span><span class="sxs-lookup"><span data-stu-id="7c17a-106">When this method returns, the offset of the byte array specified when creating a new <xref:System.IO.MemoryStream> object.</span></span> <span data-ttu-id="7c17a-107">如果位元組陣列是由 <xref:System.IO.MemoryStream>所建立，則包含0。</span><span class="sxs-lookup"><span data-stu-id="7c17a-107">Contains 0 if the byte array was created by <xref:System.IO.MemoryStream>.</span></span>

- <span data-ttu-id="7c17a-108">`length` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="7c17a-108">`length` <xref:System.Int32></span></span>\
  <span data-ttu-id="7c17a-109">當這個方法傳回時，就是記憶體資料流程內的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="7c17a-109">When this method returns, the number of bytes within the memory stream.</span></span>

## <a name="remarks"></a><span data-ttu-id="7c17a-110">備註</span><span class="sxs-lookup"><span data-stu-id="7c17a-110">Remarks</span></span>

> [!WARNING]
> <span data-ttu-id="7c17a-111">`MemoryStream.InternalGetOriginAndLength` 方法是內部的，而且不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="7c17a-111">The `MemoryStream.InternalGetOriginAndLength` method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7c17a-112">在任何情況下，Microsoft 不支援在生產應用程式中使用此方法。</span><span class="sxs-lookup"><span data-stu-id="7c17a-112">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="7c17a-113">需求</span><span class="sxs-lookup"><span data-stu-id="7c17a-113">Requirements</span></span>

<span data-ttu-id="7c17a-114">**命名空間：** <xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="7c17a-114">**Namespace:** <xref:System.IO></span></span>

<span data-ttu-id="7c17a-115">**元件：** mscorlib （在 mscorlib.dll 中）</span><span class="sxs-lookup"><span data-stu-id="7c17a-115">**Assembly:** mscorlib.dll (in mscorlib.dll)</span></span>

<span data-ttu-id="7c17a-116">**.NET Framework 版本：** 自2.0 開始提供。</span><span class="sxs-lookup"><span data-stu-id="7c17a-116">**.NET Framework versions:** Available since 2.0.</span></span>
