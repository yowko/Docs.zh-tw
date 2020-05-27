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
ms.openlocfilehash: 25fb3278e576ebe4a538379918e868b2e5f87911
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007867"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="9eb2b-102">CorElementType 列舉</span><span class="sxs-lookup"><span data-stu-id="9eb2b-102">CorElementType Enumeration</span></span>

<span data-ttu-id="9eb2b-103">指定通用語言執行時間 <xref:System.Type> 、類型修飾詞，或元資料類型簽章中類型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="9eb2b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9eb2b-104">Syntax</span></span>

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

## <a name="members"></a><span data-ttu-id="9eb2b-105">成員</span><span class="sxs-lookup"><span data-stu-id="9eb2b-105">Members</span></span>

|<span data-ttu-id="9eb2b-106">成員</span><span class="sxs-lookup"><span data-stu-id="9eb2b-106">Member</span></span>|<span data-ttu-id="9eb2b-107">描述</span><span class="sxs-lookup"><span data-stu-id="9eb2b-107">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="9eb2b-108">內部使用。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-108">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="9eb2b-109">Void 類型。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-109">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="9eb2b-110">布林值類型</span><span class="sxs-lookup"><span data-stu-id="9eb2b-110">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="9eb2b-111">字元類型。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-111">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="9eb2b-112">帶正負號的1位元組整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-112">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="9eb2b-113">不帶正負號的 1 位元整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-113">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="9eb2b-114">帶正負號的2位元組整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-114">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="9eb2b-115">不帶正負號的2位元組整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-115">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="9eb2b-116">帶正負號的4位元組整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-116">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="9eb2b-117">不帶正負號的4位元組整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-117">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="9eb2b-118">帶正負號的8位元組整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-118">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="9eb2b-119">不帶正負號的8位元組整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-119">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="9eb2b-120">4位元組浮點數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-120">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="9eb2b-121">8位元組浮點數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-121">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="9eb2b-122">System.string 類型。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-122">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="9eb2b-123">指標類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-123">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="9eb2b-124">參考型別修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-124">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="9eb2b-125">實值型別修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-125">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="9eb2b-126">類別類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-126">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="9eb2b-127">類別變數類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-127">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="9eb2b-128">多維度陣列型別修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-128">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="9eb2b-129">泛型型別的類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-129">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="9eb2b-130">具型別參考。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-130">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="9eb2b-131">原生整數的大小。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-131">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="9eb2b-132">不帶正負號的原生整數大小。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-132">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="9eb2b-133">函式的指標。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-133">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="9eb2b-134">System.object 類型。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-134">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="9eb2b-135">一維、零下限陣列類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="9eb2b-136">方法變數類型修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-136">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="9eb2b-137">C 語言所需的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-137">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="9eb2b-138">C 語言選用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-138">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="9eb2b-139">內部使用。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-139">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="9eb2b-140">類型無效。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-140">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="9eb2b-141">內部使用。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-141">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="9eb2b-142">類型修飾詞，這是可變數數目之參數清單的 sentinel。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="9eb2b-143">內部使用。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-143">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9eb2b-144">備註</span><span class="sxs-lookup"><span data-stu-id="9eb2b-144">Remarks</span></span>

<span data-ttu-id="9eb2b-145">類型修飾詞會形成代表更複雜類型的基礎。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="9eb2b-146">`CorElementType`型別修飾詞值會套用至緊接在型別簽章中的值後面。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="9eb2b-147">在類型修飾詞值之後的值 `CorElementType` 可以是 `CorElementType` 簡單類型值、元資料標記或其他值，如下表中所指定。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="9eb2b-148">所有數位（*數位*、*引數計數*、*元資料標記*、順*位*、*計數*和系*結）都會*儲存為壓縮整數。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="9eb2b-149">如需詳細資訊，請參閱 ECMA 網站上的[標準 ECMA-335-通用語言基礎結構（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm) 。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="9eb2b-150">類型修飾詞</span><span class="sxs-lookup"><span data-stu-id="9eb2b-150">Type modifier</span></span>|<span data-ttu-id="9eb2b-151">格式</span><span class="sxs-lookup"><span data-stu-id="9eb2b-151">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="9eb2b-152">ELEMENT_TYPE_PTR\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="9eb2b-152">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="9eb2b-153">ELEMENT_TYPE_BYREF\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="9eb2b-153">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="9eb2b-154">ELEMENT_TYPE_VALUETYPE\<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="9eb2b-154">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="9eb2b-155">ELEMENT_TYPE_CLASS\<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="9eb2b-155">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="9eb2b-156">ELEMENT_TYPE_VAR\<number></span><span class="sxs-lookup"><span data-stu-id="9eb2b-156">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="9eb2b-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN></span><span class="sxs-lookup"><span data-stu-id="9eb2b-157">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="9eb2b-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> .。。\<argN></span><span class="sxs-lookup"><span data-stu-id="9eb2b-158">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="9eb2b-159">ELEMENT_TYPE_FNPTR\<complete signature for the function, including calling convention></span><span class="sxs-lookup"><span data-stu-id="9eb2b-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="9eb2b-160">ELEMENT_TYPE_SZARRAY\<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="9eb2b-160">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="9eb2b-161">ELEMENT_TYPE_MVAR\<number></span><span class="sxs-lookup"><span data-stu-id="9eb2b-161">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="9eb2b-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="9eb2b-162">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="9eb2b-163">E_T_CMOD_OPT\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="9eb2b-163">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="9eb2b-164">需求</span><span class="sxs-lookup"><span data-stu-id="9eb2b-164">Requirements</span></span>

<span data-ttu-id="9eb2b-165">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9eb2b-165">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9eb2b-166">**標頭：** Corhdr.h。h</span><span class="sxs-lookup"><span data-stu-id="9eb2b-166">**Header:** CorHdr.h</span></span>

<span data-ttu-id="9eb2b-167">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9eb2b-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9eb2b-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9eb2b-168">See also</span></span>

- [<span data-ttu-id="9eb2b-169">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="9eb2b-169">Metadata Enumerations</span></span>](metadata-enumerations.md)
