---
title: 成員 (F#)
description: '深入了解 F # 程式語言中的物件成員。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a37f14d138cc017cf78e3a0ff1d5b5bba2f09020
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="members"></a><span data-ttu-id="35f67-103">成員</span><span class="sxs-lookup"><span data-stu-id="35f67-103">Members</span></span>

<span data-ttu-id="35f67-104">本節描述 F# 物件類型的成員。</span><span class="sxs-lookup"><span data-stu-id="35f67-104">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="35f67-105">備註</span><span class="sxs-lookup"><span data-stu-id="35f67-105">Remarks</span></span>
<span data-ttu-id="35f67-106">「成員」是作為類型定義的一部分且以 `member` 關鍵字宣告的功能。</span><span class="sxs-lookup"><span data-stu-id="35f67-106">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="35f67-107">F# 物件類型 (例如記錄、類別、差別聯集、介面和結構) 支援成員。</span><span class="sxs-lookup"><span data-stu-id="35f67-107">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="35f67-108">如需詳細資訊，請參閱[記錄](../records.md)、[類別](../classes.md)、[差別聯集](../discriminated-Unions.md)、[介面](../interfaces.md)和[結構](../structures.md)。</span><span class="sxs-lookup"><span data-stu-id="35f67-108">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="35f67-109">成員一般構成類型的公用介面，因此除非另外指定，否則成員為公用。</span><span class="sxs-lookup"><span data-stu-id="35f67-109">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="35f67-110">成員也可以宣告為私用或內用。</span><span class="sxs-lookup"><span data-stu-id="35f67-110">Members can also be declared private or internal.</span></span> <span data-ttu-id="35f67-111">如需詳細資訊，請參閱[存取控制](../access-Control.md)。</span><span class="sxs-lookup"><span data-stu-id="35f67-111">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="35f67-112">類型的簽章也可以用來公開或不公開類型的特定成員。</span><span class="sxs-lookup"><span data-stu-id="35f67-112">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="35f67-113">如需詳細資訊，請參閱[簽章](../signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="35f67-113">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="35f67-114">只與類別搭配使用的私用欄位和 `do` 繫結，並不是真正的成員，因為它們永遠不是類型之公用介面的一部分，也不是以 `member` 關鍵字宣告，但本節中也會加以描述。</span><span class="sxs-lookup"><span data-stu-id="35f67-114">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="35f67-115">相關主題</span><span class="sxs-lookup"><span data-stu-id="35f67-115">Related Topics</span></span>


|<span data-ttu-id="35f67-116">主題</span><span class="sxs-lookup"><span data-stu-id="35f67-116">Topic</span></span>|<span data-ttu-id="35f67-117">描述</span><span class="sxs-lookup"><span data-stu-id="35f67-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="35f67-118">類別中的 `let` 繫結</span><span class="sxs-lookup"><span data-stu-id="35f67-118">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="35f67-119">描述類別中私用欄位和函式的定義。</span><span class="sxs-lookup"><span data-stu-id="35f67-119">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="35f67-120">類別中的 `do` 繫結</span><span class="sxs-lookup"><span data-stu-id="35f67-120">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="35f67-121">描述物件初始設定程式碼的規格。</span><span class="sxs-lookup"><span data-stu-id="35f67-121">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="35f67-122">屬性</span><span class="sxs-lookup"><span data-stu-id="35f67-122">Properties</span></span>](properties.md)|<span data-ttu-id="35f67-123">描述類別和其他類型中的屬性成員。</span><span class="sxs-lookup"><span data-stu-id="35f67-123">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="35f67-124">索引屬性</span><span class="sxs-lookup"><span data-stu-id="35f67-124">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="35f67-125">描述類別和其他類型中的類似陣列屬性。</span><span class="sxs-lookup"><span data-stu-id="35f67-125">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="35f67-126">方法</span><span class="sxs-lookup"><span data-stu-id="35f67-126">Methods</span></span>](methods.md)|<span data-ttu-id="35f67-127">描述作為類型成員的函式。</span><span class="sxs-lookup"><span data-stu-id="35f67-127">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="35f67-128">建構函式</span><span class="sxs-lookup"><span data-stu-id="35f67-128">Constructors</span></span>](constructors.md)|<span data-ttu-id="35f67-129">描述初始化型別物件的特殊函式。</span><span class="sxs-lookup"><span data-stu-id="35f67-129">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="35f67-130">運算子多載</span><span class="sxs-lookup"><span data-stu-id="35f67-130">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="35f67-131">描述型別之自訂運算子的定義。</span><span class="sxs-lookup"><span data-stu-id="35f67-131">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="35f67-132">事件</span><span class="sxs-lookup"><span data-stu-id="35f67-132">Events</span></span>](events.md)|<span data-ttu-id="35f67-133">描述 F# 中的事件定義和事件處理支援。</span><span class="sxs-lookup"><span data-stu-id="35f67-133">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="35f67-134">明確欄位：`val` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="35f67-134">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="35f67-135">描述類型中未初始化欄位的定義。</span><span class="sxs-lookup"><span data-stu-id="35f67-135">Describes the definition of uninitialized fields in a type.</span></span>|
