---
description: '-可為 null (c # 編譯器選項) '
title: '-可為 null (c # 編譯器選項) '
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: 68857d0cb4d0cd1177506e0b7ce897d2cfc3aa5b
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099220"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="671f9-103">-可為 null (c # 編譯器選項) </span><span class="sxs-lookup"><span data-stu-id="671f9-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="671f9-104">**-可為 null** 的選項可讓您指定可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="671f9-104">The **-nullable** option lets you specify the nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="671f9-105">語法</span><span class="sxs-lookup"><span data-stu-id="671f9-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="671f9-106">引數</span><span class="sxs-lookup"><span data-stu-id="671f9-106">Arguments</span></span>

<span data-ttu-id="671f9-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="671f9-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="671f9-108">指定 `+` 或 **-nullable** 會導致編譯器啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="671f9-108">Specifying `+`, or **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="671f9-109">指定 `-` ，如果您未指定 **-可為 null**，則會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="671f9-109">Specifying `-`, which is in effect if you don't specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="671f9-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="671f9-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="671f9-111">指定可為 null 的內容選項。</span><span class="sxs-lookup"><span data-stu-id="671f9-111">Specifies the nullable context option.</span></span> <span data-ttu-id="671f9-112">類似于 `+` 或 `-` ，表示要啟用和停用，但允許更多的可為 null 內容的精確程度。</span><span class="sxs-lookup"><span data-stu-id="671f9-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="671f9-113">`enable`引數的作用與您指定 **-nullable** 的相同，可啟用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="671f9-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="671f9-114">指定 `disable` 將會停用可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="671f9-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="671f9-115">提供 `warnings` 引數（ **可為 null：警告**）時，會啟用可為 null 的警告內容。</span><span class="sxs-lookup"><span data-stu-id="671f9-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="671f9-116">當指定 `annotations` 引數（ **-nullable：注釋**）時，可為 null 注釋內容已啟用。</span><span class="sxs-lookup"><span data-stu-id="671f9-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="671f9-117">備註</span><span class="sxs-lookup"><span data-stu-id="671f9-117">Remarks</span></span>

<span data-ttu-id="671f9-118">流程分析用來推斷可執行程式碼內變數的可 null 性。</span><span class="sxs-lookup"><span data-stu-id="671f9-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="671f9-119">變數的推斷 null 屬性與變數宣告的可 null 性無關。</span><span class="sxs-lookup"><span data-stu-id="671f9-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="671f9-120">即使是有條件地省略方法呼叫，也會進行分析。</span><span class="sxs-lookup"><span data-stu-id="671f9-120">Method calls are analyzed even when they're conditionally omitted.</span></span> <span data-ttu-id="671f9-121">例如， <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 在發行模式中。</span><span class="sxs-lookup"><span data-stu-id="671f9-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="671f9-122">以下列屬性標注之方法的調用也會影響流程分析：</span><span class="sxs-lookup"><span data-stu-id="671f9-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="671f9-123">簡單的前置條件： <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="671f9-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="671f9-124">簡單的後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="671f9-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="671f9-125">條件式後置條件： <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> 和 <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="671f9-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="671f9-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> 例如， (`DoesNotReturnIf(false)` <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) 和 <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="671f9-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="671f9-127">成員後置條件： <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> 和 <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="671f9-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

> [!IMPORTANT]
> <span data-ttu-id="671f9-128">全域可為 null 的內容不適用於產生的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="671f9-128">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="671f9-129">無論這項設定為何，任何標示為已產生的原始程式檔都會 *停用* 可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="671f9-129">Regardless of this setting, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="671f9-130">有四種方式可將檔案標示為已產生：</span><span class="sxs-lookup"><span data-stu-id="671f9-130">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="671f9-131">在 editorconfig 中，指定 `generated_code = true` 套用至該檔案的區段。</span><span class="sxs-lookup"><span data-stu-id="671f9-131">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="671f9-132">在 `<auto-generated>` 檔案 `<auto-generated/>` 頂端的批註中放入或。</span><span class="sxs-lookup"><span data-stu-id="671f9-132">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="671f9-133">它可以位於批註中的任何一行，但批註區塊必須是檔案中的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="671f9-133">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="671f9-134">使用 *TemporaryGeneratedFile_* 開始檔案名</span><span class="sxs-lookup"><span data-stu-id="671f9-134">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="671f9-135">以 *. designer.cs*、 *. generated.cs*、 *. g.cs* 或 *g.i.cs* 的檔案名結尾。</span><span class="sxs-lookup"><span data-stu-id="671f9-135">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="671f9-136">產生器可以使用預處理器指示詞來加入宣告 [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) 。</span><span class="sxs-lookup"><span data-stu-id="671f9-136">Generators can opt-in using the [`#nullable`](../preprocessor-directives/preprocessor-nullable.md) preprocessor directive.</span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="671f9-137">若要在專案中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="671f9-137">To set this compiler option in a project</span></span>

<span data-ttu-id="671f9-138">編輯 *.csproj* 檔案，以在階層 `<Nullable>` 中新增標記 `Project/PropertyGroup` ：</span><span class="sxs-lookup"><span data-stu-id="671f9-138">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="671f9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="671f9-139">See also</span></span>

- [<span data-ttu-id="671f9-140">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="671f9-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="671f9-141">`#nullable` 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="671f9-141">`#nullable` preprocessor directive</span></span>](../preprocessor-directives/preprocessor-nullable.md)
- [<span data-ttu-id="671f9-142">可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="671f9-142">Nullable reference types</span></span>](../../nullable-references.md)
