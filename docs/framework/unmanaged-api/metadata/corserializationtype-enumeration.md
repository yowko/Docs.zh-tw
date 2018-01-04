---
title: "CorSerializationType 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSerializationType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSerializationType
helpviewer_keywords: CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e43151b1611f5b9b8218d30ba46a9143f463c193
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="e4080-102">CorSerializationType 列舉</span><span class="sxs-lookup"><span data-stu-id="e4080-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="e4080-103">指定如何將物件序列化 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="e4080-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4080-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4080-104">Syntax</span></span>  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="e4080-105">成員</span><span class="sxs-lookup"><span data-stu-id="e4080-105">Members</span></span>  
  
|<span data-ttu-id="e4080-106">成員</span><span class="sxs-lookup"><span data-stu-id="e4080-106">Member</span></span>|<span data-ttu-id="e4080-107">描述</span><span class="sxs-lookup"><span data-stu-id="e4080-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="e4080-108">物件序列化為未定義。</span><span class="sxs-lookup"><span data-stu-id="e4080-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="e4080-109">將物件序列化為布林型別</span><span class="sxs-lookup"><span data-stu-id="e4080-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="e4080-110">將物件序列化為字元類型。</span><span class="sxs-lookup"><span data-stu-id="e4080-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="e4080-111">物件會序列化為 1 位元組帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="e4080-112">物件會序列化為 1 位元組不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="e4080-113">物件會序列化為 2 位元組帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="e4080-114">物件會序列化為 2 位元組不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="e4080-115">物件會序列化為 4 位元組帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="e4080-116">物件會序列化為 4 位元組不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="e4080-117">物件會序列化為 8 位元組帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="e4080-118">物件會序列化為 8 位元組不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="e4080-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="e4080-119">物件會序列化為 4 位元組浮點數。</span><span class="sxs-lookup"><span data-stu-id="e4080-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="e4080-120">物件會序列化為 8 位元組浮點數。</span><span class="sxs-lookup"><span data-stu-id="e4080-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="e4080-121">將物件序列化為 System.String 類型。</span><span class="sxs-lookup"><span data-stu-id="e4080-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="e4080-122">將物件序列化為一維，下限為零的陣列。</span><span class="sxs-lookup"><span data-stu-id="e4080-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="e4080-123">將物件序列化為泛型類型。</span><span class="sxs-lookup"><span data-stu-id="e4080-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="e4080-124">物件會序列化為標記的物件。</span><span class="sxs-lookup"><span data-stu-id="e4080-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="e4080-125">物件會序列化為欄位。</span><span class="sxs-lookup"><span data-stu-id="e4080-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="e4080-126">物件會序列化為屬性。</span><span class="sxs-lookup"><span data-stu-id="e4080-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="e4080-127">物件會序列化為列舉型別。</span><span class="sxs-lookup"><span data-stu-id="e4080-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4080-128">需求</span><span class="sxs-lookup"><span data-stu-id="e4080-128">Requirements</span></span>  
 <span data-ttu-id="e4080-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4080-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4080-130">**標頭：** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e4080-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e4080-131">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4080-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4080-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="e4080-132">See Also</span></span>  
 [<span data-ttu-id="e4080-133">中繼資料列舉</span><span class="sxs-lookup"><span data-stu-id="e4080-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
