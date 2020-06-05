---
title: '-nullable （c # 編譯器選項）'
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: a68255dba18a022784cd4aaf0027c371893c577b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84449810"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="ae6be-102">-nullable （c # 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="ae6be-102">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="ae6be-103">**-Nullable**選項可讓您指定所需的可為 null 內容。</span><span class="sxs-lookup"><span data-stu-id="ae6be-103">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae6be-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae6be-104">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="ae6be-105">引數</span><span class="sxs-lookup"><span data-stu-id="ae6be-105">Arguments</span></span>

<span data-ttu-id="ae6be-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="ae6be-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="ae6be-107">指定 `+` 或**可為 null**，會使編譯器啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="ae6be-107">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="ae6be-108">指定 `-` ，如果您未指定 **-nullable**，則會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="ae6be-108">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="ae6be-109">`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`</span><span class="sxs-lookup"><span data-stu-id="ae6be-109">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="ae6be-110">指定可為 null 的內容選項。</span><span class="sxs-lookup"><span data-stu-id="ae6be-110">Specifies the nullable context option.</span></span> <span data-ttu-id="ae6be-111">類似于 `+` 或 `-` ，可啟用和停用，但允許更細微的可為 null 內容的精確程度。</span><span class="sxs-lookup"><span data-stu-id="ae6be-111">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="ae6be-112">`enable`引數的作用與您指定 **-nullable**相同，會啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="ae6be-112">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="ae6be-113">指定 `disable` 將會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="ae6be-113">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="ae6be-114">提供 `warnings` 引數時，**可為 null：警告**，可為 null 警告內容已啟用。</span><span class="sxs-lookup"><span data-stu-id="ae6be-114">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="ae6be-115">當指定 `annotations` 引數時，**可為 null**的注釋內容已啟用。</span><span class="sxs-lookup"><span data-stu-id="ae6be-115">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae6be-116">備註</span><span class="sxs-lookup"><span data-stu-id="ae6be-116">Remarks</span></span>

<span data-ttu-id="ae6be-117">流程分析是用來推斷可執行程式碼中變數的 null 屬性。</span><span class="sxs-lookup"><span data-stu-id="ae6be-117">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="ae6be-118">變數的推斷 null 屬性與變數的宣告 null 屬性無關。</span><span class="sxs-lookup"><span data-stu-id="ae6be-118">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="ae6be-119">方法呼叫即使有條件地省略也會進行分析。</span><span class="sxs-lookup"><span data-stu-id="ae6be-119">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="ae6be-120">例如， <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 在發行模式中。</span><span class="sxs-lookup"><span data-stu-id="ae6be-120">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="ae6be-121">以下列屬性標注之方法的調用也會影響流程分析：</span><span class="sxs-lookup"><span data-stu-id="ae6be-121">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="ae6be-122">簡單的前置條件： <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="ae6be-122">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="ae6be-123">簡單的後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="ae6be-123">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="ae6be-124">條件式後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="ae6be-124">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="ae6be-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>（例如 `DoesNotReturnIf(false)` 適用于 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ）和<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="ae6be-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (e.g. `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="ae6be-126">成員後置條件： <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="ae6be-126">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="ae6be-127">若要在專案中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="ae6be-127">To set this compiler option in a project</span></span>

<span data-ttu-id="ae6be-128">編輯 *.csproj* ，在階層內加入 `<Nullable>` 標記 `Project/PropertyGroup` ：</span><span class="sxs-lookup"><span data-stu-id="ae6be-128">Edit the *.csproj* to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="ae6be-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae6be-129">See also</span></span>

- [<span data-ttu-id="ae6be-130">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="ae6be-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ae6be-131">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="ae6be-131">Nullable reference types</span></span>](../../nullable-references.md)
