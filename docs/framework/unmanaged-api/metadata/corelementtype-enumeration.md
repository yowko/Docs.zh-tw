---
title: CorElementType 列舉
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
ms.openlocfilehash: 0ce84e1545523302cd47e60b9f047bc470e6bf0f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443623"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="03466-102">CorElementType 列舉</span><span class="sxs-lookup"><span data-stu-id="03466-102">CorElementType Enumeration</span></span>

<span data-ttu-id="03466-103">指定 common language runtime <xref:System.Type>、類型修飾詞，或元資料類型簽章中類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="03466-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="03466-104">語法</span><span class="sxs-lookup"><span data-stu-id="03466-104">Syntax</span></span>

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a><span data-ttu-id="03466-105">Members</span><span class="sxs-lookup"><span data-stu-id="03466-105">Members</span></span>

|<span data-ttu-id="03466-106">成員</span><span class="sxs-lookup"><span data-stu-id="03466-106">Member</span></span>|<span data-ttu-id="03466-107">描述</span><span class="sxs-lookup"><span data-stu-id="03466-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="03466-108">在內部使用。</span><span class="sxs-lookup"><span data-stu-id="03466-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="03466-109">Void 類型。</span><span class="sxs-lookup"><span data-stu-id="03466-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="03466-110">布林值類型</span><span class="sxs-lookup"><span data-stu-id="03466-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="03466-111">字元類型。</span><span class="sxs-lookup"><span data-stu-id="03466-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="03466-112">帶正負號的1位元組整數。</span><span class="sxs-lookup"><span data-stu-id="03466-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="03466-113">不帶正負號的 1 位元整數。</span><span class="sxs-lookup"><span data-stu-id="03466-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="03466-114">帶正負號的2位元組整數。</span><span class="sxs-lookup"><span data-stu-id="03466-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="03466-115">不帶正負號的2位元組整數。</span><span class="sxs-lookup"><span data-stu-id="03466-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="03466-116">帶正負號的4位元組整數。</span><span class="sxs-lookup"><span data-stu-id="03466-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="03466-117">不帶正負號的4位元組整數。</span><span class="sxs-lookup"><span data-stu-id="03466-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="03466-118">帶正負號的8位元組整數。</span><span class="sxs-lookup"><span data-stu-id="03466-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="03466-119">不帶正負號的8位元組整數。</span><span class="sxs-lookup"><span data-stu-id="03466-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="03466-120">4位元組浮點數。</span><span class="sxs-lookup"><span data-stu-id="03466-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="03466-121">8位元組浮點數。</span><span class="sxs-lookup"><span data-stu-id="03466-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="03466-122">System.string 類型。</span><span class="sxs-lookup"><span data-stu-id="03466-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="03466-123">指標類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="03466-124">參考型別修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="03466-125">實值型別修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="03466-126">類別類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="03466-127">類別變數類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="03466-128">多維度陣列型別修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="03466-129">泛型型別的類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="03466-130">具型別參考。</span><span class="sxs-lookup"><span data-stu-id="03466-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="03466-131">原生整數的大小。</span><span class="sxs-lookup"><span data-stu-id="03466-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="03466-132">不帶正負號的原生整數大小。</span><span class="sxs-lookup"><span data-stu-id="03466-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="03466-133">函式的指標。</span><span class="sxs-lookup"><span data-stu-id="03466-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="03466-134">System.object 類型。</span><span class="sxs-lookup"><span data-stu-id="03466-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="03466-135">一維、零下限陣列類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="03466-136">方法變數類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="03466-137">C 語言所需的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="03466-138">C 語言選用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="03466-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="03466-139">在內部使用。</span><span class="sxs-lookup"><span data-stu-id="03466-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="03466-140">類型無效。</span><span class="sxs-lookup"><span data-stu-id="03466-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="03466-141">在內部使用。</span><span class="sxs-lookup"><span data-stu-id="03466-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="03466-142">類型修飾詞，這是可變數數目之參數清單的 sentinel。</span><span class="sxs-lookup"><span data-stu-id="03466-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="03466-143">在內部使用。</span><span class="sxs-lookup"><span data-stu-id="03466-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="03466-144">備註</span><span class="sxs-lookup"><span data-stu-id="03466-144">Remarks</span></span>

<span data-ttu-id="03466-145">類型修飾詞會形成代表更複雜類型的基礎。</span><span class="sxs-lookup"><span data-stu-id="03466-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="03466-146">`CorElementType` 型別修飾詞值會套用至緊接在型別簽章中的值後面。</span><span class="sxs-lookup"><span data-stu-id="03466-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="03466-147">在 `CorElementType` 的類型修飾詞值之後的值可以是 `CorElementType` 的簡單類型值、元資料標記或其他值，如下表所指定。</span><span class="sxs-lookup"><span data-stu-id="03466-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="03466-148">所有數位（*數位*、*引數計數*、*元資料標記*、順*位*、*計數*和系*結）都會*儲存為壓縮整數。</span><span class="sxs-lookup"><span data-stu-id="03466-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="03466-149">如需詳細資訊，請參閱 ECMA 網站上的[標準 ECMA-335-通用語言基礎結構（CLI）](https://go.microsoft.com/fwlink/?LinkID=116487) 。</span><span class="sxs-lookup"><span data-stu-id="03466-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="03466-150">類型修飾詞</span><span class="sxs-lookup"><span data-stu-id="03466-150">Type modifier</span></span>|<span data-ttu-id="03466-151">格式</span><span class="sxs-lookup"><span data-stu-id="03466-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="03466-152">ELEMENT_TYPE_PTR \<`CorElementType` 值 ></span><span class="sxs-lookup"><span data-stu-id="03466-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="03466-153">ELEMENT_TYPE_BYREF \<`CorElementType` 值 ></span><span class="sxs-lookup"><span data-stu-id="03466-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="03466-154">ELEMENT_TYPE_VALUETYPE \<`mdTypeDef` 元資料標記 ></span><span class="sxs-lookup"><span data-stu-id="03466-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="03466-155">ELEMENT_TYPE_CLASS \<`mdTypeDef` 元資料標記 ></span><span class="sxs-lookup"><span data-stu-id="03466-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="03466-156">ELEMENT_TYPE_VAR \<號碼 ></span><span class="sxs-lookup"><span data-stu-id="03466-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="03466-157">ELEMENT_TYPE_ARRAY \<`CorElementType` 值 > \<排名 > \<count1 > \<bound1 > ... \<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="03466-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="03466-158">ELEMENT_TYPE_GENERICINST \<`mdTypeDef` 元資料標記 > \<引數計數 > \<arg1 > ... \<...Argn ></span><span class="sxs-lookup"><span data-stu-id="03466-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="03466-159">ELEMENT_TYPE_FNPTR \<函式的完整簽章，包括呼叫慣例 ></span><span class="sxs-lookup"><span data-stu-id="03466-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="03466-160">ELEMENT_TYPE_SZARRAY \<`CorElementType` 值 ></span><span class="sxs-lookup"><span data-stu-id="03466-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="03466-161">ELEMENT_TYPE_MVAR \<號碼 ></span><span class="sxs-lookup"><span data-stu-id="03466-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="03466-162">ELEMENT_TYPE_\<`mdTypeRef` 或 `mdTypeDef` 元資料標記 ></span><span class="sxs-lookup"><span data-stu-id="03466-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="03466-163">E_T_CMOD_OPT \<`mdTypeRef` 或 `mdTypeDef` 元資料標記 ></span><span class="sxs-lookup"><span data-stu-id="03466-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="03466-164">需求</span><span class="sxs-lookup"><span data-stu-id="03466-164">Requirements</span></span>

<span data-ttu-id="03466-165">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03466-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="03466-166">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="03466-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="03466-167">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03466-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="03466-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03466-168">See also</span></span>

- [<span data-ttu-id="03466-169">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="03466-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
